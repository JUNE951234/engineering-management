---
created: 2025/05/20 12:59
updated: 2025/11/19 16:34
aliases:
  - 设计结构矩阵
  - 结构设计矩阵
  - dsm
  - DSM
---
[剑桥工具 |工程设计中心工具包](https://www-edc.eng.cam.ac.uk/resources/tools)
Cambridge Advanced Modeller 

[DSMweb](https://dsmweb.org/home-2/)


4、计算 CI 识别标准模块

在进行CI的计算时，首先需要借用一个工具**DSM(design structure matrix，[[设计结构矩阵]])**，老师在讲这块内容时，相对比较快，但是对于一个新的概念，的确需要时间理解和深入学习，所以我就直接找到了这种方法的源头，搜集了大量的素材和工具。

Don Steward于1981年首次发表了[[设计结构矩阵]]（DSM）的公式，以此过程为重点，围绕这项研究形成了一个完整的社区，在这些年的持续推动下，基于矩阵的复杂性管理研究已经取得了长足的进步，尤其是在麻省理工学院和剑桥大学工程设计中心两个顶尖名校的推动下；DSM能够在一个域内对一种类型的依赖关系进行建模和分析，例如，对于产品，可以考虑域“组件”，使用关系类型“组件1的更改导致组件2的更改”，可以分析组件的整体更改影响，以便对可能的更改传播进行建模；DSM可以具有不同的性质：二进制DSM仅表示关系的存在，而数值DSM表示一个数值（也称为“权重”）来表示关系的强度(CI就是完全借用这种分析逻辑)。DSM可以是定向的（如下图所示，这里是从行的Task1去分析对列的影响），也可以是非定向的；DSM从来都不是自反的，也就是说，不允许从一个元素到同一个元素的关系（中间部分蓝色方框，不允许参与分析）；该图显示了一个简单的过程，由六个任务组成，在右侧显示为流程图，在左侧显示表示该过程的DSM；有许多算法可以分析DSM中关系的整体结构，例如撕裂、带状和分割，或分析不同的结构属性。

![图片](https://mmbiz.qpic.cn/mmbiz_png/qzH8g4yVnR6hJiaNFHIgrTUapwAIdZ9ibkzxZRHLJd8FQBdzibwmN2ffm5q16Wj38BU4FKIeDLkHN40RTwqrM7ICA/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1)

[[设计结构矩阵]]（DSM，也称为依赖结构矩阵）是表示和分析各种应用领域中系统模型的通用方法，DSM是指正方形矩阵（即它具有相等数量的行和列）系统中元素之间的关系，由于许多系统的行为和价值在很大程度上取决于其组成要素之间的相互作用，近年来，需求侧管理变得越来越有用和重要。与其他系统建模方法相比(如依赖图、优先矩阵、贡献矩阵、邻接矩阵、可达矩阵和N平方图，也与非矩阵方法相关，例如有向图、方程组、体系结构图和其他依赖模型)，DSM有两个主要优点：

- 它提供了一种简单而简洁的方法来代表一个复杂的系统
    
- 它提供了强大的分析力量，例如集群（以促进模块化）和排序（以最大限度地降低流程中的成本和进度风险）
    

早期的工作使用图形进行系统建模，尽管在管理复杂结构时使用图形是公认的。例如，考虑一个由三个元素（或子系统）组成的系统：元素“A”、元素“B”和元素“C”；DSM的工作假设是，出于建模目的，这三个元素完全描述了系统并表征了其行为。可以绘制一个图形来形象地表示该系统，系统图是通过允许图上的顶点/节点表示系统元素和连接两个节点的边来表示两个系统元素之间的关系来构造的，从一个元素到另一个元素的影响方向性由箭头而不是简单的链接捕捉；结果图称为有向图或简单的有向图。

![图片](https://mmbiz.qpic.cn/mmbiz_png/qzH8g4yVnR6hJiaNFHIgrTUapwAIdZ9ibkLcvtsDvCX5icicqmxO4EZMs2Un3QD2Kyeia9KWq34q8TUNyhMMVbTJicYQ/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1)

有向图（即有向图）的矩阵表示具有以下属性：

- 它是二进制的（即只填充了零和一的矩阵）
    
- 它是方形的（即具有相等行数和列数的矩阵）
    
- 它有n行和n列（n是有向图的节点数）
    
- 它有k个非零元素，其中（k是有向图中的边数）
    

在系统的二进制矩阵表示中，矩阵的对角线元素在描述系统时没有任何解释，因此它们通常要么留空要么涂黑，尽管许多人认为这些对角线单元代表节点本身是直观的；二进制矩阵在系统建模中很有用，因为它们可以表示系统中元素对之间是否存在关系，以一种形式化的方法提供了一种定性的依赖建模方法；矩阵也可以表示加权相关性，在这种情况下数字的使用DSM；同样，可以使用附加列来表示元素的权重。

![图片](https://mmbiz.qpic.cn/mmbiz_png/qzH8g4yVnR6hJiaNFHIgrTUapwAIdZ9ibkbndQ2jYkNdo5wquBoa96bztMw9uG3VuuJRLCNstV1dOUysNuy3xPaQ/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1)

如果系统是由一组要执行的任务表示的项目，那么DSM的一列中的非对角线标记表示执行与该列对应的任务所需输出的所有任务（即，读取一列以查看任务的输入，这些输入是其他任务的输出），类似地，沿特定行读取可显示哪些任务从对应于该行的任务接收信息（即沿行读取以查看任务的输出到哪里成为其他任务的输入）；在许多情况下，矩阵中任务的顺序与时间轴相对应，在这种情况下，对角线上方的标记表示将信息转发给后续（即下游）任务，这种标记称为前向标记或前向信息链接。对角线下方的标记描绘了反馈给先前列出的任务的信息（即反馈标记），并指示上游任务依赖于下游任务。请注意，并非所有DSM都是这样编写的；而“行影响列”的惯例在一些地区盛行，例如老师在讲解时，建议我们编辑时使用列影响行的思路。描述系统元素之间关系有三个基本构建块：并行（或并发）、顺序（或依赖）和耦合（或相互依赖）。

![图片](https://mmbiz.qpic.cn/mmbiz_png/qzH8g4yVnR6hJiaNFHIgrTUapwAIdZ9ibkPFXw9Q9OGiaGemM3moHFN7WqXbcC99KYrooZ2Szw5s7Ln7g1ibicBpAZw/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1)

在并行配置中，系统元素彼此之间不交互（至少对于有向图中表示的表示类型不交互）。理解单个元素的行为可以让我们更好地理解系统的行为。如果系统是一个项目，那么系统元素就是要执行的项目任务，通常关系是任务之间的定向信息交换。因此，任务B被称为独立于任务A，两个活动之间不需要进行信息交换。

- 在顺序配置中，一个元素以单向方式影响另一个元素的行为或决策。例如，元件B的设计参数是根据元件A的设计参数选择的。就项目任务而言，任务A应先于任务B执行
    
- 在耦合系统中，影响或信息流相互交织：元素A影响B，元素B影响A。如果参数A在不知道参数B的情况下无法确定（具有确定性），而B在不知道A的情况下也无法确定，就会发生这种情况。这种循环依赖性称为“循环”
    

DSM中表示的四种不同的常见类型的数据，然而，任何其他类型的DSM也是可能的；

|             |           |                      |
| ----------- | --------- | -------------------- |
| **DSM数据关系** | **代表**    | **应用**               |
| 基于组件(产品)    | 组件/模块的关系  | 系统架构、工程和设计           |
| 基于人(组织)     | 组织单位的关系   | 组织设计、界面管理、团队整合       |
| 基于活动(流程)    | 活动输入/输出关系 | 流程改进、项目调度、迭代管理、信息流管理 |
| 基于参数(低层级流程) | 设计参数关系    | 低级活动排序和过程构建，排序设计决策   |

基于组件的DSM是最常见的，因此也是这里学习的重点，基于组件的DSM记录了复杂系统架构中元素之间的交互，DSM中可以显示不同类型的交互，但交互类型因项目而异，下表显示了一些具有代表性的交互类型：

|   |   |
|---|---|
|空间|两个元素之间相邻或方向的需要|
|能源|两个元素之间的能量传递/交换需求|
|信息|两个元素之间的数据或信号交换需求|
|材料/物质|两个元件之间的材料交换需求|

当然这也不是分类的全部，随着研究和应用的增多，也可以进行其他分类，参考图表

|       |                                              |
| ----- | -------------------------------------------- |
| 械稳态   | 部件之间存在物理接触，它们相互施加稳态机械载荷，这是一种对称关系。            |
| 机械动力学 | 组件通过波动力或位移进行接触和相互作用，这可能是一种定向关系。              |
| 空间    | 组件相互接触或相邻，方向很重要，这是一种对称关系。                    |
| 热稳定状态 | 两个组件之间存在稳态温差，这可能是一种定向关系。                     |
| 热动力学  | 两个组件之间的温差波动，这可能是一种定向关系。                      |
| 电信号   | 信号从一个组件传递到另一个组件，这可能是一种定向关系。                  |
| 电气接地  | 两个部件之间有电气接地连接，这可能是一种定向关系。                    |
| 电气动力学 | 一个组件的物理设计或逻辑驱动行为连接到另一个的物理设计和逻辑行为，这可能是一种定向关系。 |

基于关系之间的影响，可以通过DSM架构，标识不同产品组成之间的影响关系，例如，考虑汽车气候控制系统组件之间的材料相互作用。在这种情况下，例如发动机风扇(B)需要将材料传输到冷凝器(E)，因为在单元(B, E)中有一个“X”。

![图片](https://mmbiz.qpic.cn/mmbiz_png/qzH8g4yVnR6hJiaNFHIgrTUapwAIdZ9ibk3yl38us4JicMKwYH2ricX6ac5diaO2w4yMmJ0Wlllqicr9LJN5QXjewCEA/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1)

图示的组件之间的相互影响比较分散，若是进行模块化规划和设计，并不符合模块设计的高内聚低耦合；现在可以重新排列矩阵，以获得高度相互作用的组件集群，同时尝试最小化集群间的相互作用；这样，数据不会改变，但是矩阵的行和列只是成对交换，以获得不同的矩阵布局；获得的分组代表了一个有用的框架，用于重新组织产品体系结构，并将重点放在模块之间的接口上；将DSM对角线上的“X”标记聚类，为气候控制系统创建了三个集群组，这些集群表示紧密相连的组件组，它们可以用来定义模块，例如，可以从不同的系统供应商订购，或者可以跨一系列不同的冰箱(例如，小、中、大容量)使用，作为携带模块，具有与其他模块(=集群)良好定义的接口，如图示；

![图片](https://mmbiz.qpic.cn/mmbiz_png/qzH8g4yVnR6hJiaNFHIgrTUapwAIdZ9ibk3yl38us4JicMKwYH2ricX6ac5diaO2w4yMmJ0Wlllqicr9LJN5QXjewCEA/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1)

从两个不同图示中，一个是按照A→B→C...排序，但影响关系分散，到上图接口和影响内聚，给模块和接口规划提供很好的思路，是如何实现呢？老师指导了方法，我也查询了一些资料，有好几种处理机制，但涉及理论比较多，这里就简单通过下图和步骤，说明在DSM的方法中，如何一步步的对DSM的矩阵进行转换。

1. 矩阵保持原来的顺序，可以看到影响关系的分析结果分布也是比较凌乱的；根据左上角的图标，知道交互和传递以行为基准，蓝色块的左侧标识直接影响，右侧标识交互的反馈(必须尽可能的减少)
    

![图片](https://mmbiz.qpic.cn/mmbiz_png/qzH8g4yVnR6hJiaNFHIgrTUapwAIdZ9ibk9FfkvBXhKsnruNSiaG4YicYOWBFias6j26UTvGjiaBKPXuJVhW7iakusKyA/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1)

3. 组件F由空列组成，表示不依赖于来自任何其他组件的信息或交互；首先在矩阵中调整组件F，并将其从进一步调整中删除(行看向上移动，列看向左侧移动)
    

![图片](https://mmbiz.qpic.cn/mmbiz_png/qzH8g4yVnR6hJiaNFHIgrTUapwAIdZ9ibkn99FwlOxdUwB4UZKXr2wicydKXMgerFPUdoUDZklPf2AEEBked1M9bg/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1)

5. 组件E由空行组成，表示不向矩阵中的任何组件提供信息或交互；将任务E排在矩阵的最后，不再考虑它(行看向下移动，列看向右侧移动)
    

![图片](https://mmbiz.qpic.cn/mmbiz_png/qzH8g4yVnR6hJiaNFHIgrTUapwAIdZ9ibkgZuereqlJ8yianNkACehdkaJnLzCpAHqHpEiaaSHrT43wFn79XIOcnmA/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1)

7. 现在，没有任务有空行或空列，因此可以分析可能存在的循环，可以从任何剩余的组件开始跟踪；在这种情况下，我们选择组件A(任意)并跟踪其对组件C的依赖关系；组件C同时依赖于来自组件A的信息；由于组件A和组件C处于一个循环中，将一个折叠成另一个，并将它们表示为单个复合组件(即组件CA)
    

![图片](https://mmbiz.qpic.cn/mmbiz_png/qzH8g4yVnR6hJiaNFHIgrTUapwAIdZ9ibkicmloEvicKPN2CfWxsXIDNYD7ia0ZialQlmmicqCxtZsJqdGpu5kteic1Ugw/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1)

9. 组件CA只有一个空列，表示它不是任何其他循环的一部分；把它排在最后，暂不再考虑它
    

![图片](https://mmbiz.qpic.cn/mmbiz_png/qzH8g4yVnR6hJiaNFHIgrTUapwAIdZ9ibklPFWgnmpPLQIOoG2j6NyMxV2fenRGQb9VeTiaNv1HWict9kpUv7EFK8g/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1)

11. 从任何计划外组件开始跟踪依赖关系：组件B依赖于组件G，而组件G又依赖于组件D，而组件D又依赖于组件B，最后的循环包括所有剩余的组件
    

![图片](https://mmbiz.qpic.cn/mmbiz_png/qzH8g4yVnR6hJiaNFHIgrTUapwAIdZ9ibkSo8icfDMpnevSxFl3r1sOYyP42vmH6VydZKYPLNW09FoYTWxZkoibzzg/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1)

13. 最终划分的矩阵(若是将B、D、G构建模块，将A、C构建模块，则发现左侧就无驱动的信息和交互)
    

![图片](https://mmbiz.qpic.cn/mmbiz_png/qzH8g4yVnR6hJiaNFHIgrTUapwAIdZ9ibkk2CtZXxdcU7X4mAbHQQuicXL9CWTWVR3oUsVziczMGMicI1xiaeUM89ibuQ/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1)

当产品比较简单时，我们可以采用手工分析的方法进行识别、规划和重组，但是若是产品结构复杂时，这个工作量，根本不是手工调整可处理的，我也在尝试使用一些工具，结合公司的产品，进行一些分析，但因为这部分研究进展很慢，所以暂时先不分享，等有比较完整的结果时；在收集的资料中，有一些工具可以参考并使用：

- 基于宏的Excel模板：这是我非常推荐的，因为这个可以满足大部分人员的使用，我也尝试使用汉字输入，目前运行还是OK的，支持常见的DSM操作(分割、撕裂、条带、模拟)
    

![图片](https://mmbiz.qpic.cn/mmbiz_png/qzH8g4yVnR6hJiaNFHIgrTUapwAIdZ9ibkWOWmI37pZIxyc8Hib3owiauKtVEhicepT3VGmbKGc69ptonHJToYQqhlg/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1)

- Cambridge Advanced Modeller 2(CAM2)是一个功能非常完善，也非常强大的DSM规划、分析和优化的工具，我也非常有幸联系到剑桥的David Wynn博士，给我提供了下载的链接，并且获取到了最新版本的软件，可惜目前只支持英文版本，我也在努力尝试理解和学习，具体资料可参考http://www-edc.eng.cam.ac.uk/cam
    

![图片](https://mmbiz.qpic.cn/mmbiz_png/qzH8g4yVnR6hJiaNFHIgrTUapwAIdZ9ibkLypWdbkYsqzcbwOLibgic7dG83CKC8HUTnUyW56czLXyonntHOuJDejw/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1)

- 也可以使用DSM Editor工具，这是一个开源的工具，地址可参考https://github.com/ajcarney/DSMEditor
    

![图片](https://mmbiz.qpic.cn/mmbiz_png/qzH8g4yVnR6hJiaNFHIgrTUapwAIdZ9ibk3p51YVc7BVq0TBBZFJRD9sTWXGpIbJ3KgbO9xxMVguobh4LbR9sKsg/640?wx_fmt=png&from=appmsg&tp=wxpic&wxfrom=5&wx_lazy=1)

- 基于MATLAB宏的专用工具，但因为目前我对MATLAB不熟悉，因此这个工具就没有进一步研究
    
- 其它包含一些商业解决方案，但都是国外产品(没有找到国内有类似的解决方案)，这些产品包括：
    

- LOOMEO，https://loomeo.com/product-architecture-management/
    
- Lattix，https://www.lattix.com/products/
    
- NDepend Dependency Matrix，Dependency Structure Matrix (ndepend.com)
    
      
    

---

这部分目前没有中文资料，基本是在一个边翻译边学习边总结和记录的状态，有点乱，但希望还是可以给大家一些收获。

**<未完待续2>**

方法论11

产品平台2

模块化2

CI3

DSM1

方法论 · 目录

上一篇一次奇妙的产品平台化开发学习之旅(1)下一篇IPD体系PLM系统落地方法杂谈(四)

阅读 602

修改于2024年09月15日

​