# DevOps Technical Practices
我们了解了DevOps的文化，方法与实践，相对比较偏理论和行动，接下来探索在技术上的应用实践。这部分涵盖了两个层级，技术实践和工具链，分别深入探讨。  
## 部署流水线 
定义运行环境并可快速重建，代码仓库，配置管理，自动化测试，自动化部署，低风险部署，数据库变更与应用变更解耦
* Product development over project development
* 版本控制
* 广泛的配置管理
* CI
* CD
* 测试自动化
* 制品管理
* 采用Trunk-Based Development分支策略
* 数据管理
* 及早引入信息安全
* 自动化
## 架构 - 微服务，面向API
* 云基础设施
* 云原生架构 - 微服务架构，面向API的设计
* 12 Factors
* 技术框架
## 监测 - 
建立测量与监控系统，基础设施，应用，日志，业务数据，流水线，告警，通知
## 度量
Goals of DevOps: Velocity, Quality, Performance。  
Deployment frequency
Deployment time
Lead time
Automated tests pass %
Defect escape rate
Availability
Service level agreements
MTTF
Mean time to detection (MTTD)
Mean time to recovery (MTTR)
Application metrics
## 建立适当的人工评审 - pull request, pair programming，轻量变更控制
## Chaos Engineering - 
通过注入故障来恢复和学习
逐渐上升的负载压力，直到服务崩溃，以便于了解各种故障模式
