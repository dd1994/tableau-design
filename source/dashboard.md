# 看板

很多可视化软件都有看板(Dashboard) 这个功能，比如 [superset](https://github.com/apache/incubator-superset) 和 [metabase](https://github.com/metabase/metabase) ：

![img](https://si.geilicdn.com/img-248f0000016daffa2df20a2166a4-unadjust_849_743.png)

![img](https://si.geilicdn.com/img-248a0000016daffa2dc70a2166a4-unadjust_780_666.png)


这种豆腐块平铺的方式虽然简单，但是有很大局限性。Tableau 既支持这种平铺式的，也支持类似 PPT 那种任意的拖拽，对富文本也有很好的支持，可以随意插图片插文本调整布局。所以在做 Tableau 的看板时，就感觉在做 PPT, 可以弄的非常漂亮。

举个例子：[中国近50年航天技术的发展](https://public.tableau.com/en-us/gallery/50-years-chinas-space-journey?tab=featured&topic=all&type=featured)

![img](https://si.geilicdn.com/img-546e0000016db00439090a211580-unadjust_1171_893.png)

你可以下载下来用Tableau 打开，会发现它只有三个 worksheet，两个简单的数字图，以及一个点图，其它的都是富文本和图片:

![img](https://si.geilicdn.com/img-4dd70000016db002a9090a2166a4-unadjust_850_792.png)

当你演讲时要做一些解释性的看板，这种能力就会相当重要。

Tableau 的看板另一个强大之处就是各种联动和筛选。它能够自定义 Actions, 最常用的就是 Filter Actions 和 Highlight Acitons, 比如点击一个图表的某一部分，可以对其它图表进行筛选或者高亮。
