# Kubernetes Downscaler

This is a helm chart for [kube-downscaler](https://codeberg.org/hjacobs/kube-downscaler) deployment.

Please refer to the [official documentation](https://codeberg.org/hjacobs/kube-downscaler#user-content-command-line-options) for its usage.

## Adding Our Chart Repository

To add the Hahow charts for your local client, run helm repo add:

```console
$ helm repo add hahow https://hahow-helm-charts.storage.googleapis.com/
```

## Installing the Chart

To install the chart with the release name `my-release`:

```console
$ helm install my-release hahow/kube-downscaler
```

The command deploys postgres exporter on the Kubernetes cluster in the default configuration. The [configuration](#configuration) section lists the parameters that can be configured during installation.

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
$ helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following table lists the configurable parameters of the Kubernetes Downscaler chart and their default values.

| Parameter | Description | Default |
| --------- | ----------- | ------- |
| `affinity` | Expressions for affinity. | `{}` |
| `defaultDowntime ` | Default time range to scale down for. | |
| `defaultUptime ` | Default time range to scale up for. | |
| `deploymentTimeAnnotation ` | Name of the annotation that would be used instead of the creation timestamp of the resource. | |
| `downscalePeriod ` | Alternative logic to scale down only in given period of time. | |
| `downtimeReplicas ` | Default value of replicas to downscale to. | |
| `excludeDeployments ` | Exclude specific deployments/statefulsets/cronjobs from downscaling. | |
| `fullnameOverride` | Override the full chart name. | `""` |
| `gracePeriod ` | Grace period in seconds for new deployments before scaling them down. | |
| `image.pullPolicy` | Image pull policy. | `IfNotPresent` |
| `image.repository` | Image repository. | `hjacobs/kube-downscaler` |
| `image.tag` | Image tag. | `nil` (Use `.Chart.AppVersion`) |
| `imagePullSecrets` | Name of Secret resource containing private registry credentials. | `[]` |
| `includeResources ` | Downscale resources of this kind. |  |
| `nameOverride` | Override the application name. | `""` |
| `namespace.activeIn` | Restrict the downscaler to work only in a single namespace | |
| `namespace.inactiveIn` | Exclude namespaces from downscaling | |
| `nodeSelector` | Node labels for pod assignment. | `{}` |
| `podSecurityContext` | Security options for pod. | `{}` |
| `replicaCount` | Number of replica. | `1` |
| `resources` | CPU/Memory resource requests/limits. | `{}` |
| `securityContext` | Security options for container. | `{}` |
| `serviceAccount.annotations	` | Additional service account annotations. | `{}` |
| `serviceAccount.create` | Specifies whether a service account should be created. | `true` |
| `serviceAccount.name` | Name of the service account. | |
| `tolerations` | Toleration labels for pod assignment. | `[]` |
| `upscalePeriod ` | Alternative logic to scale up only in given period of time. | |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```console
$ helm install my-release \
  --set serviceAccount.name=kube-downscaler  \
    hahow/kube-downscaler
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example,

```console
$ helm install my-release -f values.yaml hahow/kube-downscaler
```
