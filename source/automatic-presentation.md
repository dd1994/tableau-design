# 图表自动推荐

这篇文章主要分析 Tableau 图表自动推荐功能是如何设计的。

Tableau 的图表自动推荐功能非常强大，远远超过同类软件，这是很多人忽视的功能，但是非常有用。一方面，对可视化不了解的小白用户，自动推荐可以帮助他们快速上手，应用可视化的最佳实践，可以避免出现瞎选图表的局面；另一方面，对于资深用户，自动推荐也可以帮助他们快速作出图表，减少很多思维负担。

首先，建议仔细阅读一下 Tableau 的论文 [Show Me: Automatic Presentation for Visual Analysis](https://www.tableau.com/sites/default/files/whitepapers/081027-infovis-showme-vfinal-fix.pdf)，它比较详细的介绍了 Tableau 自动推荐的原理和交互。

Tableau 的自动推荐主要由三部分组成：

1. Automatic Marks: 自动选择 Mark 的类型
2. Add to Sheet：在左侧 Data 栏双击字段名(或者右键 Add to Sheet)会将字段自动加入到 view 中
3. buiding views from scratch for multiple fields: 作图开始前，按住 shift 键，选中多个字段，然后在 Show Me 中选择图表


## 如何自动推荐

还是建议你看 Tableau 的论文 [Show Me: Automatic Presentation for Visual Analysis](https://www.tableau.com/sites/default/files/whitepapers/081027-infovis-showme-vfinal-fix.pdf), 引用查理·芒格的话说: "I have nothing to add".
