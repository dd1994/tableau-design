# 计算字段

这篇文章主要分析 Tableau 计算字段(Calculated Fields)的设计。

## 计算字段的种类

Tableau 的计算字段主要分两种，一种是 Basic Calulations， 最后都转成 SQL 执行了查询，另一种是 Table Calculations，在前端对已经取得的数据进行计算。简单理解就是一个是后端计算，一个是前端计算。另外 LOD Expressions 显然也属于后端计算。

计算字段的分类如下：

![img](https://si.geilicdn.com/img-3f960000016da9f39d4b0a2166a4-unadjust_188_203.png)

### Basic Calulation

本质上来说，计算字段的作用就是减少手写 SQL。比如 `select sum(fieldA)*10 from tableA group by id`, 很难在 UI 上直接描述乘以 10 这个操作，如果没有计算字段的话，只能直接写 SQL 了。计算字段可以看成一个 mini 版的 SQL，非常灵活。

### Table Caculation

Table Caculation 属于前端计算，在某些场景下特别有用。这里有个例子： [中国近50年航天技术的发展](https://public.tableau.com/en-us/gallery/50-years-chinas-space-journey?tab=featured&topic=all&type=featured)。在求每个点的 X 和 Y 坐标时，严重依赖了 Table Caculation.

### LOD Expressions

LOD Expressions 需要单独拎出来说一下，这是个非常聪明的想法，极大的简化了一类复杂的问题。

Level of Detail 从 SQL 的角度很容易理解，就是 group by 的东西不一样。虽然 Tableau 官网上的文档一直避免出现 SQL 里的概念，但是如果我们从 SQL 的角度来理解 LOD Expressions 确实非常直观。如何通过 SQL 语句实现 LOD 里的 fixed, include, exclude ？ 我在网上找到[一篇非常好的例子](https://community.tableau.com/docs/DOC-18211)，它很好的说明了 LOD 的原理。

