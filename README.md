# k8s实践(四)：Controller
**环境说明：**

 
| 主机名 | 操作系统版本 | ip | docker version | kubelet version | 配置 | 备注 |
| :------: | :------:  | :------: | :------: | :------: | :------: |:------: |
| master | Centos 7.6.1810 | 172.27.9.131 |Docker 18.09.6 | V1.14.2 | 2C2G | 备注 |
| node01 | Centos 7.6.1810 | 172.27.9.135 |Docker 18.09.6 | V1.14.2 | 2C2G | 备注 |
| node02 | Centos 7.6.1810 | 172.27.9.136 |Docker 18.09.6 | V1.14.2 | 2C2G | 备注 |


<br>
&emsp; &emsp; Controller Manager由kube-controller-manager和cloud-controller-manager组成，是Kubernetes的大脑，它通过apiserver监控维护整个集群的状态，比如故障检测、自动扩展、滚动更新等并确保集群处于预期的工作状态。
&emsp; &emsp; cloud-controller-manager 在 Kubernetes 启用 Cloud Provider 的时候才需要，用来配合云服务提供商的控制，如：Node Controller、Route Controller、Service Controller。
&emsp; &emsp; Controller Manager是Kubernetes集群内部的管理控制中心， 负责Kubernetes集群内的Node、 Pod、服务端点、 服务、 资源配额、 命名空间 、服务账号等资源的管理 、 自动化部署、健康监测， 并对异常资源执行自动化修复， 确保集群各资源始终处于预期的工作状态 。 比如， 当某个Node意外若机时，Controller Manager会根据资源调度策略选择集群内其他节点自动部署原右机节点上的Pod副本 。
&emsp; &emsp; Controller Manager是 一 个控制器集合， 包含Replication Controller、Deployment Controller、RelicaSet、StatefulSet Controller、Daemon Controller、CronJob Controller、Node Controller、Resourcequota Controller 、Namespace Controller 、ServiceAccount Controller 、Token Controller、Service Controller及Endpoint Controller等多个控制器，Controller Manager是这些控制器的核心管理者。 一般来说， 智能系统和自动系统通常会通过一个操纵系统来不断修正系统的状态。 在Kubernetes集群中， 每个控制器的核心工作原理就是：每个控制器通过API服务器来查看系统的运行状态， 并尝试着将系统状态从“ 现有状态 ”修正到“期望状态”。


**文章目录：**
# 一、Kubernetes核心组件
## 1. 核心组件概述
## 2. 查看核心组件
# 二、Controller Manager
## 1. 简介
## 2. 原理
# 三、ReplicationController
## 1. 简介
## 2. 创建ReplicationController
## 3. 查看ReplicationController
## 4. 扩缩容
## 5. 删除pod
## 6. 删除ReplicationController
## 7. 标签
# 四、ReplicaSet
## 1. 简介
## 2. 创建ReplicaSet
## 3. 查看ReplicaSet
## 4. 删除ReplicaSet
# 五、Deployment
## 1. 简介
## 2. Deployment实践
# 六、DaemonSet
## 1. 简介
## 2. 创建DaemonSet
## 3. 查看DaemonSet
## 4. 更新DaemonSet
## 5. 回滚DaemonSet
## 6. 删除DaemonSet
# 七、 Job
## 1. 简介
## 2. 创建job
## 3. 查看job
## 4. 并行job
## 5. Cronjob
## 6. 删除job

<br>
<br>

**详细搭建过程及测试：**

https://blog.51cto.com/3241766/2420421
