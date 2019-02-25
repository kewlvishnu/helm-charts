# Telegraf-DS

Taken from [https://github.com/influxdata/tick-charts/tree/master/telegraf-ds](https://github.com/influxdata/tick-charts/tree/master/telegraf-ds) and added rbac rules to it, as influxdata seems to ignore the existance of RBAC for whatever reason.

[Telegraf](https://github.com/influxdata/telegraf) is a plugin-driven server agent written by the folks over at [InfluxData](https://influxdata.com) for collecting & reporting metrics. This chart runs a DaemonSet of Telegraf instances to collect host level metrics for your cluster.

## Introduction

This chart bootstraps a `telegraf-ds` deployment on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Telegraf Configuration

This chart deploys the following by default:

- `telegraf` (`telegraf-ds`) running in a daemonset with the following plugins enabled
  * [`cpu`](https://github.com/influxdata/telegraf/tree/master/plugins/inputs/system)
  * [`disk`](https://github.com/influxdata/telegraf/tree/master/plugins/inputs/system)
  * [`docker`](https://github.com/influxdata/telegraf/tree/master/plugins/inputs/docker)
  * [`diskio`](https://github.com/influxdata/telegraf/tree/master/plugins/inputs/system)
  * [`kernel`](https://github.com/influxdata/telegraf/tree/master/plugins/inputs/system)
  * [`kubernetes`](https://github.com/influxdata/telegraf/tree/master/plugins/inputs/kubernetes)
  * [`mem`](https://github.com/influxdata/telegraf/tree/master/plugins/inputs/system)
  * [`processes`](https://github.com/influxdata/telegraf/tree/master/plugins/inputs/system)
  * [`swap`](https://github.com/influxdata/telegraf/tree/master/plugins/inputs/system)
  * [`system`](https://github.com/influxdata/telegraf/tree/master/plugins/inputs/system)

## Configuration
|         Parameter                      |       Description                                         |          Default                                              |
|----------------------------------------|-----------------------------------------------------------|---------------------------------------------------------------|
| `image.repository`                     | Container image                                           | `telegraf`                                                    |
| `image.tag`                            | Container tag                                             | `1.8.3-alpine`                                                |
| `image.pullPolicy`                     | Container pull policy                                     | `IfNotPresent`                                                |
| `rbac.create`                          | Whether to create RBAC resources or not                   | `true`                                                        |
| `resources.requests.memory`            | Initial memory request                                    | `256Mi`                                                       |
| `resources.requests.cpu`               | Initial cpu request                                       | `0.1`                                                         |
| `resources.limits.memory`              | Memory limit                                              | `2Gi`                                                         |
| `resources.limits.cpu`                 | cpu limit                                                 | `1`                                                           |
| `config.agent`                         | config for the telegraf agent                             | check [values.yaml](values.yaml)                              |
| `config.outputs`                       | list of outputs for telegraf                              | check [values.yaml](values.yaml) (defaults to influx)         |
| `config.inputs`                        | list of inputs for telegraf                               | check [values.yaml](values.yaml) (defaults to k8s and docker) |
