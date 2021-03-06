---
layout: post
title:  "也聊中台"
date:   2019-10-11 18:08:40 +0800
categories: Architecture
---


#### 背景

最早听到“中台”这个词的时候算比较晚了，大概是2018年下半年，当时是在关注的某个公众号里面看到的一个文章，当时并没有在意，就是大概快速浏览了一遍，没有怎么深入理解。最近就是因为要选一个技术分享的主题，并且越来越多人在讨论“中台”，并且我也很好奇这样一个存在。于是决定带大家了解一下，中台到底是什么？

中台最早被互联网从业者关注，一定要算阿里巴巴提出的中台战略。我查阅了很多资料，我觉得最靠谱的一种说法是：故事从2015年马云走访Suppercell开始说起，但是这个只能算是一个契机，阿里巴巴的中台化进程，在这之前就已经开始了。所以要想真正理解阿里巴巴中台产生的原因，需要回到更早的时候。在2008年，阿里巴巴战略调整，天猫商城出现了。但是因为天猫相较于淘宝，有它自身的特点，同时也有很多相同之处，所以天猫和淘宝出现了重复建设的问题。比如，订单系统，支付系统，物流等等都在很大程度上属于重复的。这个现象就是所谓的烟囱式系统架构。烟囱式系统架构就是基于单个项目建设，是垂直的体系结构，每个项目都有自己的一套系统。它造成了大量的重复建设和资源浪费。如何破？就像写代码一样，稍微有一点代码洁癖的人都会把相同的逻辑抽象出来，供多次调用。系统也是如此，最自然的方法就是将重复的组织和系统进行整合。正因为如此，阿里共享事业部正式诞生，负责将前台系统中的公共部分进行平台化改造，经历了一段痛苦的摸索之后，借聚划算爆发的契机，才真正奠定了阿里共享事业部的重要地位，从此处埋下了阿里大中台的种子。

接下来就是这个契机，2015年，马云带领阿里高管团队拜访了位于芬兰，号称是世界上最成功的移动游戏公司Suppercell。我对游戏了解不多，维基百科结果：

```
Supercell（超级细胞）是一家芬兰赫尔辛基的电子游戏开发商。公司成立于2010年。知名的作品包括《卡通农场》、《部落冲突》、《海岛奇兵》、《部落冲突：皇室战争（Clash Royale)》《荒野乱斗(Brawl Stars) 》。
```

我听说过这几个游戏貌似都听过。据说Suppercell的开发模式是：一般来说两个员工，或者五个员工，最多不超过七个员工组成独立的开发团队，成为cell。团队决定自己做什么产品，然后以最快的实践退出产品公测版，看游戏是否受用户欢迎。如果不欢迎，迅速放弃这个产品，再进行新的尝试，期间几乎没有管理角色的介入。这种强大的业务试错能力是Suppercell相比于其他游戏公司最大的差别，也就是最核心的竞争力。如此快速的试错能力离不开Suppercell所构建的“中台”能力，抛开个人水平低的影响，Suppercell在多年游戏阳阿中积累了非常科学的研发方法论和体系。说到这里不知道你会不会后背发凉了呢？如果你的竞争对手有如此强大的试错能力，你觉得你10106加班加点加通宵，你干的过对手吗？

#### 我们为什么要关心企业的组织架构调整？

##### 企业自身发展的规模持续创新的需求

如果说互联网上半场是随着移动互联网带来的消费端用户的数字化转型，互联网下半场就是随着产业互联网带来的供给端数字化转型。

着眼于组织架构的调整，为什么大家都强调AI，大数据，云服务的重要地位呢？因为这些都是这些年竞争沉淀下来的成熟通用的企业能力。也是企业数字化转型过程中最先需要的最重要的基础能力。

##### 为了适迎接的更大的挑战

在过去大部分互联网公司都是赶上了互联网用户爆发的红利，快速、快速扩张，在这个过程中，技术则一直起支撑的角色，被业务拖着走，只能做到基本满足需求， 不拖后腿就已经很好了，技术架构上各方面的考量，代码质量，协同，规范等等，在一个个卡死的deadline面前，都是在做各种各样的妥协让步。技术债是越来越重，俗话说，出来混，早晚要还的。

* 2018年9月30日，腾讯宣布了7年来最大规模的组织变革，新成立了云与智慧产业群（CSIG）。同时，腾讯新成立了技术委员会，宣布未来将打造技术中台。
* 2018年11月26日，阿里宣布进行组织升级，阿里云事业群升级为阿里云智能事业群，将中台智能化与阿里云全面结合。
* 2018年12月211日，京东集团人力资源部发布关于京东商城组织架构调整的公告，公告内容称：在新的组织架构下，京东商城将围绕以客户为中心，划分为前中后台。中台为前台业务运营和创新提供专业能力的共享平台职能。
* 2018年11月26日，据36氪报道，美团正在尝试打通美团APP平台，大众点评，膜拜各个业务之间的数据，构建数据中台。
* 2019年3月19日，字节跳动也被爆出正在搭建直播大中台，抖音、西瓜视频、火山小视频这3款APP的直播技术和运营团队将被抽出、合并，支撑旗下所有的直播产品。
* 2017年12月01日，滴滴执行总裁赖春波进行了主题为《如何构建滴滴出行业务中台》的精彩演讲。
* 2018年下半年爱奇艺开始规划做推荐中台，上线仅10天，效率提升30%
* 小米集团信息化中台战略（业务+数据+技术）
* 华为“大平台炮火支撑精兵作战”企业战略，“让听得见炮声的人来决策”，”让一线直接呼唤炮火“

#### 中台是什么

##### 中台就是企业级能力复用平台

- 企业级

中台只有在拥有多个业务部门，多条业务线的企业才适用。更贴切的说法是多产品团队。建设中台一定是站在多个产品业务线之上审视，寻找可复用的能力，并进行沉淀的，达到数据，资源等各种能力的共享，复用，从而消除部门之间的业务，数据孤岛，助力企业快速变革，提升企业规模化持续创新的能力。

中台的建设过程是自下而上，由点到面的。但是建设驱动力一定是自上而下全面的上帝视角的。为什么呢？因为只有自上而下才能发现可复用的能力在哪，并且要有强有力的话语权。而建设过程是从下而上由点到面的逐步建成，最后铺开，全局支撑。所以建设中台的难点在于做好组织架构调整，它牵扯到利益的重新分配，影响面积会更大更难，是中台建设的阻力重点。

中台的概念爆发是一种趋势，越来越多的企业原本是由于创新能力才做大做强站在浪潮之巅，然而随着逐渐壮大，却失去了本应引以为傲的创新能力，或者说企业内部缺少创新的土壤，引起企业运营效率下降等问题。所以企业上帝视角的跨部门夸业务的支撑能力的中台建设就被提升到了企业的战略高度。

- 复用和去重

去重和复用常常被同时提起，`去重`讲的更多是想后看，是技术驱动的；`复用`讲的更多是向前看，是业务和用户驱动的。两个实操难度也不同，做到`去重`已经很困难了，能关注到`复用`就更少。

总结几条：

1. 复用是中台更加关注的目标；
2. 可复用性和易复用性是衡量中台建设优劣的重要指标；
3. 业务响应力和业务满意度也是考核中台建设进程的重要标准。

实现更好的复用，一方面将更高抽象的通用的业务逻辑通过抽象后下沉到中台，这样前台就会更轻，学习成本和开发维护成本更低，越能更快的适应业务变化；缺点是，抽象级别越高，越难被复用，需要架构师对于各业务有深入理解和非常强的抽象能力。另一方面就是通过对于中台能力的SaaS化包装，减少前台团队发现中台能力和使用中台能力的阻力，甚至通过自助式的方式就快速定位和使用中台能力。目前很多企业在阐释的内部API集市或者数据商店就是在这方面的努力和尝试。

##### 数据业务双中台

![典型企业中台架构](/home/ice/projects/hexo-ablog/ablog/source/_posts/ali_dt_middleoffice.jpg)
{% asset_img ali_dt_middleoffice.jpg %}

这是阿里提出的一个组织架构的形式，业务中台和数据中台共同构成双中台，撑起所有前台的业务。业务中台将后台资源进行抽象封装整合，转化为前台友好的课重用的共享的和兴能力，实现了后端业务资源到前台易用的能力转化。

数据中台是从后台以及业务中将数据引入，完成海量数据的存储，计算，产品化包装，构成企业的核心数据能力，为前台基于数据的定制化创新和业务中台基于数据反馈的持续演进提供强大支撑。业务/数据中台相辅相成，互相支撑，共同构成成强大的后方炮火群和雷达阵。

##### 技术中台

技术中台就是将使用云或者其他基础设施的能力以及应用各种技术中间件的能力进行整合和包装，过滤掉技术细节，提供简单一致，易于使用的应用技术基础设施的能力接口，助力前台和业务中台数据中台的快速建设。

##### 研发中台

软件开发是一项工程，涉及到管理，流程，测试，团队协作等方面，如果和将企业的开发流程最佳实践沉淀成可重用的能力，从而助力创新性应用的快速开发迭代，所以，研发中台就是关注开发效率、开发能力管理（开发效能管理）的平台。

如果说技术中台为前台提供了基础设施重用的能力，那么研发中台就为前台应用提供了流程和质量管控以及持续交付的能力。总之，开发效能是构建前中台应用过程中必不可少的重要一环。

如果将技术中台比喻成前台特种兵的武器装备，那效能中台就是前台特种兵的管理训练基地以及可以快速将战士运送到一线战场的激动运输部队。

##### 组织中台

如果说架构的设计拆分都是对现实世界的一种虚拟，虚拟的架构必须要和现实中对应的，否则架构就会出问题。

中台战略的成功，能否实现技术架构与组织架构的匹配，是一道绕不过去，却一定要跨过去的门槛。从阿里成立共享事业部，海尔的人单合一模式，再到腾讯的组织架构重构，他们都在向这个方向努力。

如果一个项目的启动，从筹划到层层审核评审，花的都是白花花的时间，在互联网瞬息万变的生存环境中，对手说不定已经APP上线了，你还在想各种策略方法应付层层领导的审视。为了真正解决企业创新在组织架构层面的摩擦和阻力，构建真正的平台组织就很有必要了。

![组织中台](/home/ice/projects/hexo-ablog/ablog/source/_posts/organization.png)

{% asset_img organization.png %}

组织中台很像企业中的内部风投和创新孵化机构，为前台组织和团队构建创新型前台应用提供类似于投资评估（项目甄别），投资管理，投后管理（孵化与风控），真正从组织和制度上支撑前台组织和应用的快速迭代，持续规模化创新。

#### 中台建设的核心价值

* 清晰业务架构，提高需求响应
* 提升软件复用，降低定制成本
* 优化系统架构，实现弹性稳定
* 管理软件资产，实现系统互通
* 清晰处理数据，提升运营效率
* 有效管理资产，降低资源成本

#### 建设中台遇到的问题

* 灵活性和稳定性的矛盾

  中台建成，对外提供服务，由于前台用户众多，一旦出现技术上的问题，影响面非常大。如果中台易用性差，还是避免不了前台继续造轮子，不用中台提供的“垃圾”服务了。

* 中台与前台的边界模糊

  在实际实践时，中台与前台往往划分不清楚，这也是一个难点。

* 人员调配问题

  中台建设过程中，企业人员也有可能会有调配变动。比如有些部门取消，人事调动，操作过程可能会有人员离职等，也会引起各职位配合不顺畅等问题。交接方：我们加班加点，辛辛苦苦做的成果却要交接给别人，心有不甘。被交接方：这个系统原来的团队写的什么东西？纯粹是一坨“垃圾”，不想成为接锅侠。

* 跨部门沟通阻力，跨部门的目标差异

  企业各部门原本都会有各自的一套目标系统。部门与部门之间的KPI一般是不相同的。而部门与部门之间的目标肯能会有竞争甚至冲突。比如一个前台部门的目标要求就是要快速灵活，对于稳定性要求不高，要的就是尽快占领市场，而中台部门的目标是服务稳定，开发流程标准等，这时候就会有冲突。

  中台部门提供服务，当然是希望需求有优先级，任务分个主次。

  前台部门又会觉得中台支持需求响应速度慢，还不如自己实现。

* 公司利益分配

  一般情况，距离业务近的地方比距离业务远的地方能分到更多公司增长的成果。中台看起来是业务，但又是公共业务，既然是公共业务，那基本上没办法分享到任一单一业务的红利。

  中台服务稳定是应该的，然而出事故很有可能是中台来背锅。如果这样，中台很有可能就成了烫手的山芋。没有更多的利益，却要承担更大的风险，反而阻碍了中台的快速迭代。

#### 企业适合建设中台吗？

* 业务规模达到一定程度

  中台是企业逐步发展，为了解决企业膨胀，重复、资源浪费等问题而逐步演化产生的，因此中台必须是拥有可沉淀的一定量级的IT资产，企业要充分复用这些IT次产才能突破当前的瓶颈，更高效地赋能企业的各个业务线，保证企业规模化持续创新。只有在企业业务和服务价值达到一定规模才会具备沉淀实施的条件，否则就是杀鸡用牛刀。

* 已经实践了系统化，中心化、平台化

  “系统化、中心化、平台化、中台化”，是一个企业在数字化道路上进化的路线，无论企业架构，技术架构都是要一路升级打怪而来的，只有这样才能找到合适的架构。如果一个企业已经成功地实践了“系统化、中心化、平台化”的过程，并比较饱和状态地支撑了前台业务，并且遇到业务发展瓶颈。那么这个企业也许可以开始考虑向“中台化”迈进了。

* 有组织架构重构的魄力

  中台是企业级别的开放共享。否则它将仅仅是一个事业部门或者分公司旗下的功能平台而已。无论BAT，还是T（头条）M（美团）D（滴滴），还有小米，京东、网易都在开始决定中台建设之际或者之前，对企业层级的组织架构做了一定的调整，有些甚至是大震动。有魄力做组织架构重构的企业，才适合快速高效地做中台建设。架构思维中同样认为，业务架构要和组织架构保持一致，否则业务架构就一定是不合理的。


#### 个人思考

关键词：沉淀、赋能、灵活、快速迭代、全局观

我觉得一个人的自我管理和成长就像是在创业，和企业管理有异曲同工之处。对于我个人，中台看似离你我很远。通过这次大面积阅读中台和架构相关的读物，让我意识到，阅读的重要性，而比阅读量更重要的是，笔记。中台的核心思想就是沉淀和赋能。

我体会最深的的就是沉淀，对于我个人，我可能会有很多阅读的计划，可能会是书，公众号文章，视频课程等等但是可能很多时候就是读完就完了，看的时候可能看的很起劲，但是过不了两个星期，基本就忘完了。做笔记，或者写一些读后感，真的很让人抓狂，当时长期积累，量变引起质变，会有好收成的。

* 沉淀

  无论是阅读、实践，重要的事多给自己找机会历练，更重要的是总结沉淀

* 赋能

  利用所处的环境，阶层，能利用的资源，全部调动起来，为我所用。

* 灵活、快速迭代

  我认为一个人的成长过程就是一个迭代的过程，沉淀的都是中长期的能力，基于各种可能性，不要否定自己，不要给自己打标签，多尝试，多赋予自己更多的可能性。

* 全局观

  跳出局限观察，上一层高度观察，再上一层高度，再上一层。。。







