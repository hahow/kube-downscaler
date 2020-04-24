# Kube-downscaler Helm chart

This is a helm chart for [kube-downscaler](https://github.com/hjacobs/kube-downscaler) deployment.

Please refer to the [official documentation](https://github.com/hjacobs/kube-downscaler#command-line-options) for its usage.

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

The following table lists the configurable parameters of the StatsD Exporter chart and their default values.

| Parameter | Description | Default |
| --------- | ----------- | ------- |

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
