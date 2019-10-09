# 基本思想和原则

Tableau 的官网和 [Papers 页面](https://research.tableau.com/papers)提供了很多文章，对理解 Tableau 的设计思想有很大帮助。

这篇文章会分析一下 Tableau 基本思想和原则，虽然看起来可能有点虚，但是这些基本原则保证了 Tableau 这个产品逻辑上的一致性，一旦你理解它的方式，就很容易举一反三，进行自我学习。后续的文章会详细解剖 Tableau 一些核心功能的设计思想，比如作图方式、智能推荐、计算字段等等。

## Tableau 的起源

要理解 Tableau 的产品设计思想，一定要先仔细阅读 [Visual Analysis for Everyone](https://www.tableau.com/sites/default/files/whitepapers/visual-analysis-for-everyone.pdf) 这篇文章，它介绍了 Tableau 的设计思想和基本原则。 这篇文章中，提到了可视化分析(Visual Analysis)这个概念:

> Tableau Software was founded on the idea that analysis
and visualization should not be isolated activities but
must be synergistically integrated into a visual analysis
process. 

这是 Tableau 这个产品思想的基础。举个反例，像 [redash](https://github.com/getredash/redash) 这样的软件，就是严格的把“可视化”和“分析”分离开，在 [redash 官网的视频](https://redash.io) 就可以看到，它的操作方式就是：先写 SQL 取得数据，然后选择图表进行可视化。


## 基本原则：

### 1.  Easy Interface
要保证简单易用的界面，这样才能给普通人使用

### 2. Data Exploration

> Tableau helps you think visually

Tableau 要帮助人们可视化的探索数据

### 3. Expressiveness

> An open set of questions cannot be addressed by a fixed set of visualization types

表达能力要强，能够提供无限种图表类型，这是基于[图形语法](https://book.douban.com/subject/10123863/)的基础，图形语法的理论直接影响了 Tableau 的交互方式， 后面会详细解释。

### 4. Visualization Best Practices

遵循可视化的最佳实践

###  5. Database Independence

数据库无关，让用户不用纠结于语法细节。这是因为 vizQL 编译到 SQL 时抹平了差异。

## VizQL

VizQL 是一种 DSL, Tableau 的核心技术，虽然不是开源的，但是我们从介绍里能看出个大概:

> like SQL and MDX, VizQLTM contains a WHERE clause for filters, an ORDER BY clause for sorting, a GROUP BY clause for controlling level of detail and aggregation, etc. VizQL is unique in that it contains a rich syntax for creating the row and column structure of a table. VizQL also lets you select different types of marks (text, symbols, lines, etc.) and control their visual attributes (color, size, etc.). VizQL has the capabilities needed to create all the common types of visualizations necessary for analysis and reporting applications. Tableau’s VizQL technology is unique within the industry.

VizQL 主要做了两件事：

1. 编译成 SQL，进行查询取数
2. 基于[图形语法](https://book.douban.com/subject/10123863/)的理论基础进行可视化

第一件事很好理解，为了抹平各种数据库的差异，需要一种中间语言。
第二件事有很多库做过了，比如[ggplot2](https://ggplot2.tidyverse.org), [Vega](https://vega.github.io/vega/), [G2](https://antv.alipay.com/zh-cn/g2/3.x/index.html)

从我个人的直观感受来说，一个 DSL 同时做这两件事是一个值得商榷的问题。



