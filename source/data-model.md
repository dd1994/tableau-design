# 数据模型

很多可视化软件只有一种数据模型，即区分`string/number/date/time...`等数据类型， 这大多是出于使用数据库自带函数的需要，比如有些函数只支持时间，有些函数只支持数字。引入额外的数据模型会极大的增加理解成本，是一个值得反复斟酌的事情。

Tableau 的数据模型有三种：

1. Dimension 和 Measure
2. Discrete 和 Continuous
3. 数据类型：string/number/date/time...

## 三种数据模型

### Dimensions and Measures

<https://www.tableau.com/sites/default/files/whitepapers/081027-infovis-showme-vfinal-fix.pdf>

```
By convention in datacubes used in data warehouses, independent variables are called dimensions and dependent variables are called measures. Measures. e.g. Sum(Sales), are typically aggregated before display (and thus calculated) and are hence dependent on the choice of fields used as a dimension. This is an important and novel aspect of Tableau’s data model.
```

<https://help.tableau.com/current/pro/desktop/en-us/datafields_typesandroles.htm>
```
Dimensions contain qualitative values (such as names, dates, or geographical data). You can use dimensions to categorize, segment, and reveal the details in your data. Dimensions affect the level of detail in the view.

Measures contain numeric, quantitative values that you can measure. Measures can be aggregated. When you drag a measure into the view, Tableau applies an aggregation to that measure 
```

从 SQL 的角度， Dimension 和 Measure 很容易理解：

* dimension: 作为 group by 后面的值
* measure: 作为 group by 时需要聚合的值，必须要加上 sum/avg 等聚合函数

我在官网找到一张图：


![img](https://si.geilicdn.com/img-4d380000016d728b77be0a211587-unadjust_881_559.png)


当你把 dimension 字段拖入上述红色框中时，从数据库的角度的来说，你就是做了一次 group by, 而将 measure 字段拖入时，就会自动加上聚合函数。

我经常在想，虽然 Tableau 声称不需要懂技术不需要懂 SQL 也能使用，但是不懂 SQL 的同学真的能够理解聚合函数和LOD等概念？Google "why tableau", 第二个提示就是为什么要聚合 measure:

![img](https://si.geilicdn.com/img-11640000016d813de5920a2166a4-unadjust_1566_334.png)

### Discrete and Continuous

Discrete: 离散数据，显示蓝色
Continuous: 连续数据，显示绿色

Discrete 和 Continuous 的字段在 Tableau 中行为有以下区别：

* 将离散字段拖到 rows/column 时显示标题，将连续字段拖入 rows/column 表现为连续的坐标轴
* 进行筛选时，离散数据可以直接选择，连续数据选择区间，这个很方便
* 将字段映射到颜色时，离散数据表现为不同的颜色，连续数据表现为渐变色
* 严重影响图表智能推荐，比如像 Mark 的 shape 属性，因为形状总数有限，只能映射离散字段。而 Size 属性基本只映射连续字段.

### Data Types

数据的类型, 在 Tableau 左侧 Data 栏字段名前面有小图标指示，大概有以下几种：

* string
* date
* date & time
* number
* boolean
* geographic values
* ...

以上这些数据类型的区分方便使用数据库内置函数时进行提示，比如某些函数只支持时间，你填个数字给你报错。

