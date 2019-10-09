# 作图方式

<!-- TOC -->

- [作图方式](#作图方式)
  - [图形语法](#图形语法)
  - [超越图形语法](#超越图形语法)

<!-- /TOC -->

去 [Tableau Gallery](https://public.tableau.com/en-us/gallery/?tab=viz-of-the-day&type=viz-of-the-day) 看看, 多翻几页，就可以直观体会到 Tableau 相比同类软件的强大，它可以做出同类软件不可能做出的图，甚至可以做出很多图表库（如 G2 和 ggplot2）都做不出来的图。这跟它基于图形语法的作图方式密切相关。

这里讲的作图方式是指作出图表的交互方式。在可视化软件中，常见的作图方式是: 

1. 拖拽或者写SQL得到表格数据
2. 在一个列表中选出你想要的图表类型(选图表这个过程可能有自动选择)
3. 配置一些图表细节

这种方式存在很大的限制，至少来说，你可以选择的图表类型是固定的。而 Tableau 基于图形语法的交互方式可以通过 Marks 的组合实现无限种图表。

## 图形语法

首先，Tableau 作图的理论是基于图形语法的，这是 Tableau 最重要的基石之一。[The Grammar of Graphics](https://book.douban.com/subject/10123863/) 是 Leland Wilkinson 写得一本书。图形语法是图表的一种抽象方式，它有很多实现：

* R语言最流行的绘图包 [ggplot2](https://ggplot2.tidyverse.org)
* [G2](https://antv.alipay.com/zh-cn/g2/3.x/index.html): 命令式编程，API 类似 ggplot2. 
* [vega/vaga-lite](https://vega.github.io/vega-lite/): JSON 配置生成图表，Python, JS 等多语言实现, [vega-lite 的柱状图示例](https://vega.github.io/editor/#/examples/vega-lite/bar)
* ...

如果你用过 G2 或者 ggplot2 作图，就很容易上手 Tableau，因为很容易理解图表可以由一个或多个 Marks 组成，也能理解[分面(Facet)](https://www.yuque.com/antv/g2-docs/tutorial-facet)的概念。

当我们作图时，已经拥有数据，要得到图表，本质上要做的事情就是将数据映射到图形的属性上。
图形的属性包括位置，颜色，大小，透明度等等。

举个例子，如果有以下数据：

```js
[{
    "Entity": "China",
    "Year": 2000,
    "Code": "CHN",
    "GDP": 22370.806
}, {
    "Entity": "China",
    "Year": 2001,
    "Code": "CHN",
    "GDP": 24236.511
}, {
    "Entity": "China",
    "Year": 2002,
    "Code": "CHN",
    "GDP": 26449.461
},{
    "Entity": "Japan",
    "Year": 2000,
    "Code": "JPN",
    "GDP": 53489.355
}, {
    "Entity": "Japan",
    "Year": 2001,
    "Code": "JPN",
    "GDP": 53706.701
}, {
    "Entity": "Japan",
    "Year": 2002,
    "Code": "JPN",
    "GDP": 53770.071
},{
    "Entity": "United States",
    "Year": 2000,
    "Code": "USA",
    "GDP": 127130.582
}, {
    "Entity": "United States",
    "Year": 2001,
    "Code": "USA",
    "GDP": 128371.354
}, {
    "Entity": "United States",
    "Year": 2002,
    "Code": "USA",
    "GDP": 130664.23
}, 
]
```

这是中美日三国各个年份的GDP 数据，如果要做出这三个国家 GDP 随时间变化的曲线，如下图：

![img](https://si.geilicdn.com/img-25a90000016d7c0325df0a21924a-unadjust_554_497.png)

在图形语法中该如何做呢？分三步

1. 将几何标记类型设置为折线(line)
2. 将字段 year 映射到 x 轴
3. 将字段 GDP 映射到 y 轴

用 G2 的语法表达就是 `chart.line().position('year*GDP').color('Entity')`, 
而用 Tableau 表达就是:

![img](https://si.geilicdn.com/img-5eeb0000016d7c094d610a219248-unadjust_1798_1176.png)

## 超越图形语法

基于图形语法的设计让 Tableau 有更强的灵活性，通过组合的方式，可以绘制出无数种图表。而不是像 Excel 那样，从几十种图表中选出一种。很多可视化软件，像 [Metabase](https://github.com/metabase/metabase) 和 [Superset](https://github.com/apache/incubator-superset) 的作图方式都是类似 Excel 的设计，这种设计虽然看上去简单，但是从源头上就没法达到更强的灵活性，很多图根本做不出来。

但是这种基于图形语法的作图方式并不是完美的，为了保持这种逻辑上的一致性，Tableau 的学习曲线会比较陡，比如它不会提供类似玫瑰图、桑基图这类东西，而是需要自己去组合，这样难度就很大了。
