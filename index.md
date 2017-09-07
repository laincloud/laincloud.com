<video width="100%" height="100%" controls>
  <source src="http://lain.oss-cn-beijing.aliyuncs.com/LAIN%20Demo%20in%205%20minutes.mp4" type="video/mp4">
</video>

### 来自宜信的诚意作品
[LAIN](https://github.com/laincloud/lain) 是来自[宜信大数据创新中心](http://cbdic.creditease.cn)的基于 Docker 技术的容器私有云平台（PaaS）。

### 来自开发者，面向开发者
LAIN 面向技术栈多样寻求高效运维方案的高速发展中的组织、DevOps 人力缺乏的创业公司，以及个人开发者。

### LAIN 的特色功能
#### 一个配置文件
LAIN的配置都集中在代码仓库的一个YAML文件里，在这里可以描述应用测试、运行、部署等不同阶段的镜像构建方式，也可以配置volumes、日志、备份、容器、编排等的参数，尽最大可能降低开发人员使用Docker的门槛。
#### 简易的服务动态伸缩
可以在LAIN配置文件中定义服务的实例数量、CPU、内存，也可在命令行或web界面上对上述参数进行动态调整。动态扩容缩容只是web界面上的简单交互。
#### 服务的自动维持和恢复
LAIN自带巡检和服务发现的特性。容器异常退出后，会自动被拉起；机器出现宕机，上面的容器会自动迁移到其它机器上。对于无法随意迁移的程序，LAIN也可通过健康检查的方式将请求路由给正常工作的程序，确保应用的可用性。
#### 配置文件管理
LAIN通过内置的[lvault](https://github.com/laincloud/lvault)组件实现了代码与配置的分离。每一个LAIN集群都有一个自带的配置中心lvault，加密存储着该集群所有应用的配置文件。只有应用管理者有权限管理应用的配置文件。用户将不同集群的配置分别写到对应的lvault中，即可将同一个镜像推送到不同的集群中部署运行。
#### 简易的日志收集
LAIN提供了完备的日志收集组件[Rebellion](https://github.com/laincloud/rebellion)。默认情况下会自动收集每个应用的标准输出和标准错误，并将其汇总到宿主机。对web类服务，LAIN会自动收集Nginx日志。
#### 完整的监控报警方案
LAIN内部集成了监控组件[Hedwig](https://github.com/laincloud/hedwig)，基于成熟开源组件实现，拥有指标收集、汇总、展示、监控等完备的监控告警功能。集群中的每台机器和大部分基础组件都在其监控范围内。开发人员也可方便地对应用数据进行监控和报警。
#### 安全的网络隔离
LAIN使用开源的[calico](https://www.projectcalico.org/)项目为集群构建了SDN网络，实现了应用内高效率的网络互通。应用间的服务互访必须显式声明，从而提供了安全的网络隔离，适用于包含敏感数据流量的私有云。
#### 统一的权限认证
LAIN内部集成了统一的权限认证组件[SSO](https://github.com/laincloud/sso)，可以管理LAIN应用的权限，并且提供了用户注册、身份认证等系列功能。SSO基于OAuth2授权架构，方便第三方应用接入。

### Latest Release

目前最新版是2.1.1。

- [下载](https://github.com/laincloud/lain/archive/v2.1.1.tar.gz)
- [Release note](https://github.com/laincloud/lain/releases/tag/v2.1.1)

### 快速安装
本地安装LAIN集群依赖VirtualBox（version >= 5.1.22）和Vagrant (version >= 1.9.4).
```shell
curl -fsSL https://github.com/laincloud/lain/archive/v2.1.1.tar.gz | tar xf -
cd lain-2.1.1
vagrant up
# Config DNS in local shell
sudo bash -c 'echo "192.168.77.201  console.lain.local" >> /etc/hosts'
```

初始化完成后即可在浏览器访问console:
```
http://console.lain.local
````

您也可以直接使用以下账户登陆我们的 demo 集群控制台: [http://demo.laincloud.com](http://demo.laincloud.com)：
- 用户名：demo，密码：laindemo
- 用户名：demo1，密码：laindemo

可以分别看到 hello-world 和 todomvc 2 个示例 LAIN 应用。在控制台里，您可以进行扩容缩容、调整 CPU 和调整内存等操作。
hello-world 和 todomvc 均提供 HTTP 服务，您可以通过 http://${appname}.${LAIN-domain} 访问，比如：
- [http://hello-world.demo.laincloud.com](http://hello-world.demo.laincloud.com)
- [http://todomvc.demo.laincloud.com](http://todomvc.demo.laincloud.com)

> - hello-world 扩容成多个示例后，LAIN 会将请求分发到不同的实例上，您可以通过刷新页面观察效果；
>   其源代码在 [https://github.com/laincloud/hello-world](https://github.com/laincloud/hello-world)
> - todomvc 的任务列表存储在服务端的数据库里，所有用户看到的是同一份数据；
>   其源代码在 [https://github.com/laincloud/todomvc](https://github.com/laincloud/todomvc)

完整的文档在 [https://docs.laincloud.com](https://docs.laincloud.com)，其中：
- [Install](https://docs.laincloud.com/install/cluster.html) 展示了
如何从头开始构建 Lain 集群
- [LAIN App Demo](https://docs.laincloud.com/tutorial/first-lain-app.html) 展示了如何在 Lain 集群上部署应用

### LAIN视频

#### 集群管理入门
<div align="center" class="videoWrapper">
<iframe width="100%" height="100%" src="https://www.bilibili.com/html/html5player.html?cid=7578012&aid=4671059" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
</div>

#### LAIN CLI使用
<div align="center" class="videoWrapper">
<iframe width="100%" height="100%" src="https://www.bilibili.com/html/html5player.html?cid=7581619&aid=4673273" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
</div>

### 了解更多
![logo](https://laincloud.com/images/lain-logo-02.svg)[LAIN White Paper](https://docs.laincloud.com)

> 也可以直接下载 [PDF](https://www.gitbook.com/download/pdf/book/laincloud/white-paper),
> [Mobi](https://www.gitbook.com/download/mobi/book/laincloud/white-paper)
> 或 [ePub](https://www.gitbook.com/download/epub/book/laincloud/white-paper)
