# Activemq

[Activemq](http://activemq.apache.org/) 

## TL;DR;

```bash
$ helm install stable/activemq-cluster
```

## Introduction

The application template will launch an [Activemq](http://activemq.apache.org/) cluster on [Kubernetes](http://kubernetes.io) using the [Helm](https://helm.sh) package management tool .

 
## Installation requirements

- Kubernetes 1.4+ and Beta APIs
- The cluster internally meets the supply of corresponding PV

## Install the app

Install the app by app name `my-release`:

```bash
$ helm install --name my-release stable/activemq-cluster
```

This command deploys a RabbitMQ cluster with a default configuration. The [configuration](#configuration) section lists all the parameters that can be used during installation..

> **Tip**: See all releases, please use the command `helm list`

## Uninstall the app

Uninstall/delete `my-release` :

```bash
$ helm delete my-release
```

This command removes all related Kubernetes components and removes the release.

## Configuration parameter

The table below lists the default values for ActiveMQ configurable parameters and parameters.

Parameter	

|         Parameter          |                       Description                       |                         Default                          |
|----------------------------|---------------------------------------------------------|----------------------------------------------------------|
| `image.image`               |  cluster image                                  | `tianctrl/activemq`                             |   
| `image.pullPolicy`               |  Mirror pull rule                                  | `IfNotPresent`                             |   
| `metrics.enabled`               |  Whether the scalar is on                                  | `false`                             |          
| `replicas`                 |  replicas number                                | `1`      |      


Use `--set key=value[,key=value]` to specify the parameters in `helm install` For Example,

```bash
$ helm install --name my-release \
  --set namespace=activemq \
    stable/activemq-cluster
```


Alternatively, you can use a file to specify parameters during the installation phase. For example,

```bash
$ helm install --name my-release -f values.yaml stable/activemq-cluster
```

JSON file example:

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

