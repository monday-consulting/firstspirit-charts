# FirstSpirit K8s Helm Chart

## Prerequisits

1. The cluster may need a image pull secret to pull the FirstSpirit image from a private repository.
2. You may need to have an image pull secret for your private image registry. Create one with:
    ```console
    $ kubectl create secret private-registry regcred --docker-server=<url.to.registry> --docker-username=<your-name> --docker-password=<your-pword> --docker-email=<your-email>
    ```
   and configure it in the chart with
    ```
    global.extraImagePullSecrets: [{ name: private-registry }]
    ```
   or by commandline
   ```
   --set global.extraImagePullSecrets[0].name=private-registry
   ```

## Add repo

`helm repo add firstspirit-charts https://monday-consulting.github.io/firstspirit-charts`

## Install chart from repo

`helm install <RELEASE_NAME> firstspirit-charts/firstspirit --set-file firstspirit.license=<path-to-license-file>`

### Upgrade running fs

`helm upgrade <RELEASE_NAME> firstspirit-chart/firstspirit --set-file firstspirit.license=secrets/fs-license.conf`

## Install chart from workspace

`helm install <RELEASE_NAME> . --set-file firstspirit.license=secrets/fs-license.conf`

### Upgrade running fs

`helm upgrade <RELEASE_NAME> . --set-file firstspirit.license=secrets/fs-license.conf`

# Parameters

## Passing custom values.yaml

To override parameters you can also supply your custom values.yaml to the helm install command by adding
`-f <path-to-custom-values>`

`helm install --version 1.3.1 firstspirit-chart/firstspirit --set-file firstspirit.license=<path-to-license-file> -f <path-to-custom-values>`

### Global parameters

| Name                            | Description                                     | Value |
|---------------------------------|-------------------------------------------------|-------|
| `global.imageRegistry`          | Global Docker image registry                    | `""`  |
| `global.extraImagePullSecrets:` | Global Docker registry secret names as an array | `[]`  |
| `global.storageClass`           | Global StorageClass for Persistent Volume(s)    | `""`  |

### General parameters

| Name                | Description                                                                                         | Value |
|---------------------|-----------------------------------------------------------------------------------------------------|-------|
| `commonAnnotations` | Common annotations to add to all resources (sub-charts are not considered). Evaluated as a template | `{}`  |
| `commonLabels`      | Common labels to add to all resources (sub-charts are not considered). Evaluated as a template      | `{}`  |

### FirstSpirit parameters

| Name                                            | Description                                                                                         | Value                   |
|-------------------------------------------------|-----------------------------------------------------------------------------------------------------|-------------------------|
| `firstspirit.license`                           | Common annotations to add to all resources (sub-charts are not considered). Evaluated as a template | `""`                    |
| `firstspirit.url`                               | Common labels to add to all resources (sub-charts are not considered). Evaluated as a template      | `http://localhost:8000` |
| `firstspirit.backupOnStop`                      | Create a backup in `/opt/backup-full`                                                               | `true`                  |
| `firstspirit.labels`                            | Labels to add to the StatefulSet. Evaluated as template                                             | `{}`                    |
| `firstspirit.podLabels`                         | Labels to add to the StatefulSet pods. Evaluated as template                                        | `{}`                    |
| `firstspirit.replicaCount`                      | Number of replicas to deploy                                                                        | `1`                     |
| `firstspirit.podAnnotations`                    | Additional pod annotations                                                                          | `{}`                    |
| `firstspirit.extraVolumes`                      | Extra volumes to add to the deployment                                                              | `[]`                    |
| `firstspirit.extraVolumeMounts`                 | Extra volume mounts to add to the container. Normally used with `extraVolumes`.                     | `[]`                    |
| `firstspirit.initContainers`                    | Extra init containers to add to the deployment                                                      | `[]`                    |
| `firstspirit.sidecars`                          | Extra sidecar containers to add to the deployment                                                   | `[]`                    |
| `firstspirit.advanced.fsServerPolicy`           | Provide a custom fs-server.policy file                                                              | `""`                    |
| `firstspirit.advanced.fsWrapperIsolated`        | Provide a custom fs-wrapper.isolated.conf file                                                      | `""`                    |
| `firstspirit.advanced.fsWrapperLicenseIsolated` | Provide a custom fs-wrapper-license.isolated.conf file                                              | `""`                    |
| `firstspirit.advanced.fsWrapperVendor`          | Provide a custom fs-wrapper-vendor.conf file                                                        | `""`                    |
| `firstspirit.advanced.fsLogging`                | Provide a custom fs-logging.conf file                                                               | `""`                    |
| `firstspirit.advanced.fsServer`                 | Provide a custom fs-server.conf file                                                                | `""`                    |
|                                                 |                                                                                                     | `""`                    |

### Traffic Exposure parameters

| Name                               | Description                                                | Value          |
|------------------------------------|------------------------------------------------------------|----------------|
| `service.type`                     | Fixed to `LoadBalancer`                                    | `LoadBalancer` |
| `service.port`                     | FirstSpirit port                                           | `8000`         |
| `service.portName`                 | FirstSpirit service port name                              | `firstspirit`  |
| `service.loadBalancerIP`           | Load balancer IP if service type is `LoadBalancer`         | `""`           |
| `service.loadBalancerSourceRanges` | Addresses that are allowed when service is LoadBalancer    | `[]`           |
| `service.annotations`              | Provide any additional annotations for FirstSpirit service | `{}`           |
| `service.serviceLabels`            | Labels for FirstSpirit service                             | `{}`           |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

## Legal Notices

FirstSpirit is a product of [Crownpeak Technology GmbH](https://www.e-spirit.com/), Dortmund, Germany.

## Disclaimer

This document is provided for information purposes only. Monday Consulting may change the contents hereof without
notice. This document is not warranted to be error-free, nor subject to any other warranties or conditions, whether
expressed orally or implied in law, including implied warranties and conditions of merchantability or fitness for a
particular purpose. Monday Consulting specifically disclaims any liability with respect to this document and no
contractual obligations are formed either directly or indirectly by this document. The technologies, functionality,
services, and processes described herein are subject to change without notice.

