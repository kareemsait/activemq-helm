# Activemq

[Activemq](http://activemq.apache.org/) 

## TL;DR;

```bash
$ helm install stable/activemq-cluster
```

## 介绍

该应用模板会使用 [Helm](https://helm.sh) 包管理工具在 [Kubernetes](http://kubernetes.io) 上启动一个 [Activemq](http://activemq.apache.org/)  集群.

## 安装要求

- Kubernetes 1.4+ 支持 Beta APIs
- 集群内部满足供给相应PV

## 安装应用

通过应用名来安装应用 `my-release`:

```bash
$ helm install --name my-release stable/activemq-cluster
```

该命令会部署一个默认配置的RabbitMQ集群.  [configuration](#configuration) 配置目录列出了所有安装期间可使用的的参数.

> **Tip**: 查看所有release请使用 helm list

## 卸载应用

卸载/删除 `my-release` :

```bash
$ helm delete my-release
```

该命令会移除所有与之相关的Kubernetes组件,并删除release.

## 配置参数

下面的表格列出了ActiveMQ可配置的参数和参数的默认值.

|         Parameter          |                       Description                       |                         Default                          |
|----------------------------|---------------------------------------------------------|----------------------------------------------------------|
| `image.image`               |  cluster image                                  | `tianctrl/activemq`                             |   
| `image.pullPolicy`               |  镜像拉取规则                                  | `IfNotPresent`                             |   
| `metrics.enabled`               |  标量是否开启                                  | `false`                             |          
| `replicas`                 |  replicas number                                | `3`      |      


使用 `--set key=value[,key=value]` 指定各个参数, 在 `helm install` 时使用. 例如,

```bash
$ helm install --name my-release \
  --set namespace=activemq \
    stable/activemq-cluster
```


或者, 可以在安装阶段使用文件来指定参数. 例如,

```bash
$ helm install --name my-release -f values.yaml stable/activemq-cluster
```

JSON文件示例：

```
{
    "name": "activemq-cluster-example",
    "namespace": "default",
    "repo": "neunn",
    "chart": "activemq-cluster",
    "version": "latest",
    "values": {
        "replicas": "3",
        "image": {
            "image": "neunnsy/activemq-metrics",
            "pullPolicy": "IfNotPresent"
        },
        "metrics": {
            "enabled": true
        }
    } 
}

```

