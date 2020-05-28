# DevOps Principles & Practices
以三步法为主线，结合持续交付，探索DevOps的原则及实践。在开始之前，我们需要确立共同的目标：以可持续的方法，低风险、高质量地快速交付。所有的原则和实践都围绕着这个终极目标展开和演进。
## 价值流
这一步的关键目标是建立从开发到运维之间快速的、平滑的、能向客户交付“价值”的工作流。那么，如何定义价值？德鲁克这么定义 -- "What the customer buys and considers value is never a product. It is always utility, that is, what a product or a service does for the customer." 这意味着在用户在使用你交付的产品或功能之前，你的工作并未完成。  
价值流的定义：“一个组织基于客户的需求所执行的一系列有序的交付活动”，或者，“为了给客户设计、生产和提供产品或服务所需从事的一系列活动，它包含了信息流和物料流的双重价值” -- Value Stream Mapping, Karen Martin & Mike Osterling。

Quality in a product or service is not what the supplier puts in. It is what the customer gets out and is willing to pay for. A product is not quality because it is hard to make and costs a lot of money, as manufacturers typically believe. This is incompetence. Customers pay only for what is of use to them and gives them value. Nothing else constitutes quality.
Peter Drucker. -- Peter Drucker
价值流原则
* 使工作可见
* 限制在制品
* 小批量 
* 减少交接次数 
* 持续识别和改善约束点
* 消除价值流中的困境和浪费
### 使工作可见
Why -  
* 易于评估进度，前置时间
* 易于识别问题，哪里在排队，哪里停滞，哪里在等待
* 提高沟通的效率，减少争议

Kanban是一项有力的工具，让交付过程的工作完全透明，所有人都可以轻松获取各项重要工作的进展，状况，潜在的问题。Kanban可根据需要做定制，让更多的工作可见，以更多的维度可见。  
Sprint计划也可以清晰展示目前的工作进展，结合Backlog，Velocity，Burndown图表，可以演化出更多维度可见性。  
具体到各个活动，可以针对产出做可视化，例如代码扫描报告，测试报告，流水线图表，性能测试报告。。。  
### 限制在制品
Why -  
* 减少工作切换
* 易于发现工作中存在的问题--为什么会等待？为什么无法完成？
* 更短的处理时间
* 减少浪费--所有未完成的工作
* 加速流动
How - 
Stop starting，Start finishing
限制未完成工作的数量，例如5
### 小批量 
Why -  
    * 更少的在制品
    * 更短的前置时间和处理时间
    * 快速暴露问题，解决问题
    * 更少的冲突
    * 更快的反馈
How -  
* 矮小精干的故事
* 限制每次交付的故事
* 频繁地提交
* 流水线快速执行
* 微服务架构
### 减少交接次数
Why -  
* 交接意味着大量的沟通
* 交接导致潜在的等待队列
* 交接存在信息的损耗
How -  
* 消除不必要的活动，减少交接的次数
* 自动化交接
* 自助服务
### 持续识别和改善约束点
Why -  
* 在任何价值流中，总是有一个流动方向、一个约束点，任何不针对此约束点而做的优化都是假象。 -- Beyond the Goal, Goldratt
How -  
1. 识别系统的约束点
2. 决定如何利用这个约束
3. 考虑全局优化
4. 改善系统约束
5. 如果约束已经突破，回到第一步
### 消除价值流中的困境和浪费
Why -  
浪费意味着支付了更高的成本，花费了更多的时间，导致交付速度缓慢
How -   
* 半成品
* 额外的工序
* 过度设计
* 额外的特性
* 任务切换
* 等待
* 移动
* 缺陷
* 非标准或手工工作
* 全职救火队员
## 反馈
反馈原则
* 在复杂系统中安全地工作
* 及时发现问题
* Swarm and solve the problems to build new knowledge
* 在源头保证质量
* 为下游工作中心优化设计 -- 内部客户，外部客户
### 在复杂系统中安全地工作
Why -  
* 软件越来越复杂
* 故障不可避免
How -  
* 复杂的工作都被管理起来，这样设计和操作层面的问题都会暴露
* 问题被及时解决，快速产生新知识
* 新知识在组织内全面推广
* 领导者培养不断这类能力的领导者
### 及时发现问题
Why -  
* 问题发现得越早，解决的成本越低
* 问题暴露得越晚，造成的影响越不可控，后果越严重
* 隐藏或绕开问题，意味着错过了学习和改善的机会
How -  
* 建立前馈回路和反馈
* 充分测试、实时监控、有效告警、广泛度量
* 每次提交都触发流水线
### 现场解决问题并创造新知识
Why -  
* 现场的状况更清晰完整，易于理解问题
* 防止把问题带入下游
* 防止启动新工作，带入新问题，让事情变得复杂
How - 
* 限定快速解决的期限
* 快速回滚
* PDCA
* 必要时引入更多资源
### 在源头保证质量
Why - 
* 质量缺陷会滚雪球，最终失控
* 质量不只是单个部门或单个角色的事情
* 质量免费
* 加速学习
How - 
* 明确DoD，请下游工作中心参与评审
* Peer Review
* Pair Programming
* 代码扫描
* 单元测试

### 为下游工作中心优化设计 -- 内部客户，外部客户
Why -  
* 下游就是你的最近的客户，也许是内部，也许是外部
* 为下游优化，产生累积效应
How -  
* 聆听下游的需求，并为之优化
* 部署，配置，监控与度量
### 建立能力模型
## 持续学习和实验
### 建立学习型组织和安全文化 - 第五项修炼
Why -  
现代社会，软件交付处于极度复杂的环境，并且在迅速变得更复杂，事故不可避免。可以避免的是糟糕的文化：病态型及官僚型。
出现事故时，"Name, Blame, Shame"的方式会导致信息封闭，逃避责任，恐惧滋生，最终导致相同的灾难一再发生。
坏苹果理论，不解决问题，只解决人。
Blame --> Fear --> Lies
How -  
* 建立学习型组织，参考<第五项修炼>。
* 建立生机型组织文化，参考<Westrum组织文化>
* 事故引发调查，关注背后的原因，改进设计
* 建立事后总结的文化，从流程、工具、共享及奖励措施等方面入手
### 制度化日常工作的改善
Why -  
* 比日常工作更重要的是对日常工作的持续改进 -- Mike Orzen
* 撤除临时措施
* 避免技术债
How -  
* 明确预留改善的时间
* 定期组织改善闪电战(Kaizen Blitze)
* 不断审视价值流
* 无止境的改善
### 局部优化转化为全局优化 - at scaling
Why -  
* 个体知识与团队知识的价值是不同，杠杆效应
* 避免重复的事故，尽量将事故消灭在萌芽阶段
* 团队之间相互促进
How -  
* 建立知识库，并对全员公开
* 所有事故的分析报告都应尽可能广泛地公开
* 推动隐性知识显性化
* 发布工具，并在工具中内置最佳实践
### 日常工作注入弹性模式 - 反脆弱性(anti-fragility) - Chaos Monkey - Chaos Engineering
Why -  
* 弹性意味着勇气，主动发起挑战
* 实验性想法
How -  
* Chaos Engineering
  * Identify top 5 critical systems
  * Choose system
  * Whiteboard the system
  * Determine what experiment you want to run:(resource, state, network)
  * Determine Blast Radius
* 模拟整个区域或数据中心故障。
* 删除Kafka某个实例的部分主题以重现生产环境发生的问题。
* 在预定的时间段内为服务间一定百分比的流量注入延迟。
* 基于Function的混沌(运行时注入): 随机引起Functions抛出异常。
* 代码插入Code insertion: 在目标程序中加入指令，允许特定的指令执行之前发生故障。
* Time travel: 强制系统时钟同步失效。
* 在驱动中执行一段代码模拟I/O错误。
* 透支某个Elasticsearch集群的CPU cores。
### 领导层强化学习文化
Why -  
* 领导力是为团队创造条件，表现卓越
How -  
* 帮助一线工作者在日常工作中发现并解决问题
* 协助一线工作者建立学习文化
