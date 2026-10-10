**姓名：** 庞祎彤
**学号：** 202413093001

# 同质性（Homophily）

## 一、定义

同质性（Homophily）是网络科学与计算社会学的基石性概念，俗称“物以类聚，人以群分”（Birds of a feather flock together）。它指的是：在社会网络中，具有相似特征、属性或立场信念的行动者之间，形成连边（如好友、关注、转发、引用）的概率显著高于特征异质者之间的连边概率。

同质性由社会学家 Paul Lazarsfeld 与 Robert K. Merton 于1954年系统提出[1]。同质性本质上描述的是一种**网络拓扑结构的形成偏好与聚类倾向**，它是回音室效应、群体极化以及信息窄化等宏观传播现象的底层结构性前提。

## 二、背景和上下文

### 2.1 理论渊源与概念分类

Lazarsfeld 与 Merton 在开创性研究中，明确将同质性区分为两个核心维度[1]：

1. **地位同质性（Status Homophily）**：基于先赋或社会外在人口统计学特征（如性别、种族、年龄、地缘、阶级）而形成的群体聚合。
2. **价值同质性（Value Homophily）**：基于个体后天的态度倾向、道德价值体系、意识形态或信念体系（如党派立场、体育公平观、道德评判偏好）而形成的连接聚集。

在 McPherson、Smith-Lovin 与 Cook（2001）的经典综述中，同质性被进一步确立为“限制受众社会世界的最深层网络原则”[2]。地理邻近、组织约束与个人自选择共同构成了其社会学成因。

### 2.2 理论核心困境：同质性选择 vs. 社会影响

在实证研究和因果推断中，同质性面临一个核心内生性难题：**网络中观察到的“朋友态度相似”，究竟是“因为相似才结交”（同质性选择，Selection），还是“因为结交后被同化”（社会影响，Influence/Contagion）？**

* **同质性选择（Selection）**：用户基于预先存在的态度主动寻找立场相同者建立连边。
* **社会影响（Social Influence）**：连边建立后，个体在邻居的持续说服与互动压力下调整自身立场。
区分这两者是计算传播学设计因果推断（如SAOM模型、反事实实验）的核心任务。

## 三、举例说明

### 案例一：政治博客引文网络的极端同质性

Adamic 与 Glance（2005）针对美国大选期间政治博客链接网络的研究，是同质性分析的里程碑[3]。研究发现，保守派与自由派博主在发帖引文时表现出极强的价值同质性，91%以上的跨博客引用仅在同阵营内部流动，跨阵营连边极其稀疏，形成了两团泾渭分明、近乎解耦的网络拓扑。

### 案例二：跨国体育争议中的“道德价值同质性”

以 2024 巴黎奥运会拳击资格争议为例：跨平台用户基于不同的道德基础（“保护女性运动员安全与公平竞争” vs. “尊重人权与反歧视保护”）自发分裂。实证抓取 X（原Twitter）与微博上的转发引用网络可见，网民的转发互动高度聚集于持有相同“道德框架”与“性别议题认知”的KOL周围，跨阵营对话仅占极小比例，展现出强烈的价值同质性聚集特征。

### 案例三：基于大规模社交网络的基线同质性测量

Halberstam 与 Knight（2016）利用 Twitter 政治沟通数据，测算了数百万用户意识形态同质性指数[4]。他们发现，政治兴趣强烈的活跃用户网络中，同质性程度高达 80% 以上，且这种基于立场的连边偏好直接导致外来信息在跨群体渗透时遭遇断崖式衰减。

## 四、对比分析

在网络与舆情研究中，“同质性”常与“回音室”和“极化”混为一谈，但三者处于完全不同的分析层次：

| 概念                               | 学科归属          | 核心侧重点                                                   | 与同质性的关系                                               |
| :--------------------------------- | :---------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| **同质性（Homophily）**            | 网络科学 / 社会学 | **微观与中观连边偏好**：节点倾向与同类相连的拓扑机制。       | **充要关系中的“必要结构条件”**：没有同质性连边，很难形成回音室。 |
| **回音室（Echo Chamber）**         | 传播学 / 政治学   | **宏观信息环境状态**：异质信息被系统性排除、内部信息循环强化。 | **宏观系统产物**：由同质性网络与算法推荐结合演化出的结构性信息孤岛。 |
| **群体极化（Group Polarization）** | 社会心理学        | **受众态度的动态偏移**：群体协商后立场向更极端方向漂移。     | **认知/心理结果**：同质性群体在频繁互动后可能引发的极化效应。 |

**辨析要点**：同质性是**关系属性**（谁与谁连接），回音室是**环境属性**（信息怎么流转），极化是**态度属性**（观点走向何方）。单有同质性不必然导致极化。

## 五、深入扩展

### 5.1 测量路径与经典指标

在实证研究中，测量网络同质性主要有两条数学路径：

#### （1）科尔曼同质性指数（Coleman's Homophily Index, $HI$）

为排除群体自身规模效应（Base Rate）的影响，评估个体是否有超越随机概率的“同类偏好”[5]：

$$HI_i = \frac{s_i - w_i}{1 - w_i}$$

其中，$s_i$ 是节点 $i$ 的邻居中同类特征节点所占的实际比例，$w_i$ 是整个网络中该特征节点所占的基线先验比例。

* 若 $HI_i > 0$，表明存在**同质性偏好**；
* 若 $HI_i = 0$，表明连边符合**随机混合（Baseline Homophily）**；
* 若 $HI_i < 0$，表明存在**异质性倾向（Heterophily）**。

#### （2）网络模块度与 assortativity 属性同配系数（Newman's Assortativity）

Newman 提出的属性混合系数 $r \in [-1, 1]$[6]：

$$r = \frac{\sum_k e_{kk} - \sum_k a_k b_k}{1 - \sum_k a_k b_k}$$

其中 $e_{kk}$ 为两端节点属性同为 $k$ 的连边比例，$a_k = \sum_l e_{kl}$，$b_k = \sum_l e_{lk}$。若 $r > 0$，全网呈现显著的同配同质性。

### 5.2 因果识别前沿：SAOM 随机行动者导向模型

在时序动态网络中，为分离**同质性选择（Selection）**与**社会同化影响（Influence）**，前沿计算社会学主要借助 Snijders 开发的 **SAOM（Stochastic Actor-Oriented Models，如 R-RSiena）**[7]。
模型将网络演化建模为马尔可夫连续时间决策过程，分别设定：

* **网络客观函数（Network Objective Function）**：参数估计用户基于同伴属性建立/断开连边的倾向（同质性效应检验）；
* **行为客观函数（Behavior Objective Function）**：参数估计用户根据已有连边邻居的平均态度调整自身立场的倾向（同化传染效应检验）。

### 5.3 跨平台算法与“算法诱导同质性”（Algorithmic Homophily）

Cinelli 等（2021）指出，平台底层架构对同质性具有重塑作用[8]：

* **信息流推荐平台（如 X / 抖音）**：协同过滤算法会精准向用户推荐“具有类似点击行为”的其他用户生成的内容，无形中放大了价值同质性；
* **主题聚合版块平台（如 Reddit）**：用户基于特定话题/子版块集聚，虽然局部版块内同质，但版块内交叉论辩机制削弱了个体间的纯粹同配连边。

### 5.4 推断边界与数据反思

不能把网络中的“同质性高”简单等同于“公众陷入全面极化”。在研究推断中必须谨记：

1. **活跃发声偏差**：社交网络中呈现极强同质性互动的往往是情绪唤醒度最高的核心活跃用户，大量温和与边缘受众处于不发声状态；
2. **负面交互缺失**：若只抓取转发网络（多为认同/同质），而忽略评论中的反驳与批驳（有符号网络，Signed Network），会人为高估同质性水平。

## 六、简明总结

同质性是描述社会与信息网络中“相似行动者优先连边”的基础拓扑规律，分为地位同质性与价值同质性[1]。它是促成回音室与群体极化的必要网络结构条件。

在量化测量上，研究通常基于属性同配系数（Assortativity）与 Coleman 同质性指数进行测定[5, 6]，并借由 SAOM 动态网络模型严格剥离“同质选择”与“社会传染”的内生因果混淆[7]。

在平台化舆论生态中，推荐算法正推动同质性从“人际自选择”演化为“算法诱导同质”[8]，而在实证研究中，必须结合有符号网络与推断边界，审慎防范由活跃偏误带来的网络同质性高估。

## 参考文献

[1] LAZARSFELD P F. Friendship as a social process: A substantive and methodological analysis[J]. Freedom and Control in Modern Society, 1954, 18(1): 18-66.
[2] MCPHERSON M, SMITH-LOVIN L, COOK J M. Birds of a feather: Homophily in social networks[J]. Annual Review of Sociology, 2001, 27(1): 415-444.
[3] ADAMIC L A, GLANCE N. The political blogosphere and the 2004 US election: divided they blog[C]//Proceedings of the 3rd international workshop on Link discovery. 2005: 36-43.
[4] HALBERSTAM Y, KNIGHT B. Homophily, group size, and the diffusion of political information in social networks: Evidence from Twitter[J]. Journal of Public Economics, 2016, 143: 73-88.
[5] COLEMAN J S. Relational analysis: The study of social organizations with survey methods[J]. Human Organization, 1958, 17(4): 28-36.
[6] NEWMAN M E J. Mixing patterns in networks[J]. Physical Review E, 2003, 67(2): 026126.
[7] SNIJDERS T A B, VAN DE BUNT G G, STEGLICH C E G. Introduction to stochastic actor-based models for network dynamics[J]. Social Networks, 2010, 32(1): 44-60.
[8] CINELLI M, DE FRANCISCI MORALES G, GALEAZZI A, et al. The echo chamber effect on social media[J]. Proceedings of the National Academy of Sciences, 2021, 118(9): e2023301118.
