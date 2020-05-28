# 工具链
随着K8s的普及，DevOps与之形成了不可分割的联合体，为IT组织提供了越来越强大的工具集。这里，我们持续关注DevOps的开源解决方案，基于私有化部署展开探讨，并对其中部分工具深入研究以更好地实践DevOps。
## Jenkins
Jenkins是目前应用最广泛的流水线工具，社区活跃，丰富的插件，极具说服力的案例，是我们推荐给客户的核心工具。
* 代码版本控制 -- GitLab/Github
* 依赖管理及构建工具 -- Maven/Gradle
* 代码扫描 -- Sonarqube
* 镜像仓库 -- Harbor, Clair
* 制品仓库 -- Nexus/JFrog Artifactory
* UI测试 -- Selenium, Appnium
* 单元测试 -- JUnit/TestNG
* 接口测试 -- Postman/Postwoman/[Katalon](https://www.katalon.com)
* 验收测试 -- Robot Framework/[Gauge](https://gauge.org)/
* 性能测试 -- JMeter/[Gatling](https://gatling.io/)
* BDD -- [RSpec](https://rspec.info)/[Cucumber](https://cucumber.io)/[Spock](http://spockframework.org)/[SpecFlow](https://specflow.org/)
* 测试管理 -- [Zephyr](https://marketplace.atlassian.com/apps/1014681/zephyr-for-jira-test-management?hosting=cloud&tab=overview)/[Xray](https://marketplace.atlassian.com/apps/1211769/xray-test-management-for-jira?hosting=cloud&tab=overview)/[TestProject]()
* 自动化测框架 -- [EPAM JDI](https://jdi.epam.com/)/[Selenide](https://selenide.org/)/[Atata Framework](https://atata.io/)/
* 容器工具 -- Docker, Kubernetes
* K8s部署工具 -- Helm, Chart Museum
* 虚拟机工具 -- Ansible/Chef/Puppet/Salt
## Jenkins X
Jenkins X是基于Kubernetes的持续集成、持续部署平台。
* 基础工具 -- Kubernetes
* 构建与部署工具
> - [Helm](https://helm.sh)  
> Helm帮助你管理K8s应用，Helm Charts帮助你定义、安装和升级K8s应用。Helm Charts易于创建、版本化、共享和发布，简化应用的发布。
> - [ChartMuseum](https://chartmuseum.com/)  
> ChartMuseum为Helm Charts提供仓库服务。
> - [Kaniko](https://github.com/GoogleContainerTools∂∂/kaniko)  
> Kaniko可以在容器或K8s集群中构建镜像，不需要Docker daemon，完全在userspace中运行，简化了镜像构建的过程。
> - [Skaffold](https://skaffold.dev)  
> Skaffold处理构建、推送和部署应用到K8s的工作流，基于目录结构，所有的dockerfile都会被处理。Skaffols用skaffold命令执行工作，也会Watch工作目录的变化，自动执行。部署过程同样依赖Helm。
> - [Draft](https://draft.sh)  
> Draft依赖Helm在K8s部署应用，反映即刻的代码变化，便于开发工程师测试和验证这个变化。Draft的目标是让开发工程师与K8s的交互更容易，在提交到Git之前，快速将代码打包并构建镜像，发布到开发环境。在开发工程师提交代码之后，部署工作将交给Helm或类似的工具。
> - [Tekton](https://tekton.dev/)  
> Tekton是K8s原生的CI/CD工具框架，可以在K8s中迅速搭建流水线。同时支持Jenkins, Jenkins X, Skaffold, Knative及其它CI/CD工具
> - Other candidates: Drone, Ko, jib, makisu, s2i, Spinnaker
## 