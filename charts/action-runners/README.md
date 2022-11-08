## Docs

All additional docs are kept in the `docs/` folder, this README is solely for documenting the values.yaml keys and values

## Values

**_The values are documented as of HEAD, to review the configuration options for your chart version ensure you view this file at the relevant [tag](https://github.com/actions-runner-controller/actions-runner-controller/tags)_**

> _Default values are the defaults set in the charts `values.yaml`, some properties have default configurations in the code for when the property is omitted or invalid_

| Key                                                      | Description                                                                                                                | Default                                                                                         |
|----------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|
| `labels`                                                 | Set labels to apply to all resources in the chart                                                                          |                                                                                                 |
| `replicaCount`                                           | Set the number of controller pods                                                                                          | 1                                                                                               |
| `webhookPort`                                            | Set the containerPort for the webhook Pod                                                                                  | 9443                                                                                            |
| `syncPeriod`                                             | Set the period in which the controller reconciles the desired runners count                                                 | 1m                                                                                             |
| `enableLeaderElection`                                   | Enable election configuration                                                                                              | true                                                                                            |
| `leaderElectionId`                                       | Set the election ID for the controller group                                                                               |                                                                                                 |
| `githubEnterpriseServerURL`                              | Set the URL for a self-hosted GitHub Enterprise Server                                                                     |                                                                                                 |
| `githubURL`                                              | Override GitHub URL to be used for GitHub API calls                                                                        |                                                                                                 |
| `githubUploadURL`                                        | Override GitHub Upload URL to be used for GitHub API calls                                                                 |                                                                                                 |
| `runnerGithubURL`                                        | Override GitHub URL to be used by runners during registration                                                              |                                                                                                 |
| `logLevel`                                               | Set the log level of the controller container                                                                              |                                                                                                 |
| `logFormat`                                               | Set the log format of the controller. Valid options are "text" and "json"                                                                              |       text                                                                                           |
| `additionalVolumes`                                      | Set additional volumes to add to the manager container                                                                     |                                                                                                 |
| `additionalVolumeMounts`                                 | Set additional volume mounts to add to the manager container                                                               |                                                                                                 |
| `authSecret.create`                                      | Deploy the controller auth secret                                                                                          | false                                                                                           |
| `authSecret.name`                                        | Set the name of the auth secret                                                                                            | controller-manager                                                                              |
| `authSecret.annotations`                                 | Set annotations for the auth Secret                                                                                        |                                                                                                 |
| `authSecret.github_app_id`                               | The ID of your GitHub App. **This can't be set at the same time as `authSecret.github_token`**                             |                                                                                                 |
| `authSecret.github_app_installation_id`                  | The ID of your GitHub App installation. **This can't be set at the same time as `authSecret.github_token`**                |                                                                                                 |
| `authSecret.github_app_private_key`                      | The multiline string of your GitHub App's private key. **This can't be set at the same time as `authSecret.github_token`** |                                                                                                 |
| `authSecret.github_token`                                | Your chosen GitHub PAT token. **This can't be set at the same time as the `authSecret.github_app_*`**                      |                                                                                                 |
| `authSecret.github_basicauth_username`                   | Username for GitHub basic auth to use instead of PAT or GitHub APP in case it's running behind a proxy API                 |                                                                                                 |
| `authSecret.github_basicauth_password`                   | Password for GitHub basic auth to use instead of PAT or GitHub APP in case it's running behind a proxy API                 |                                                                                                 |
| `dockerRegistryMirror`                                   | The default Docker Registry Mirror used by runners.                                                                        |                                                                                                 |
| `hostNetwork`                                            | The "hostNetwork" of the controller container                                                                              | false                                                                                           |
| `image.repository`                                       | The "repository/image" of the controller container                                                                         | summerwind/actions-runner-controller                                                            |
| `image.tag`                                              | The tag of the controller container                                                                                        |                                                                                                 |
| `image.actionsRunnerRepositoryAndTag`                    | The "repository/image" of the actions runner container                                                                     | summerwind/actions-runner:latest                                                                |
| `image.actionsRunnerImagePullSecrets`                    | Optional image pull secrets to be included in the runner pod's ImagePullSecrets                                            |                                                                                                 |
| `image.dindSidecarRepositoryAndTag`                      | The "repository/image" of the dind sidecar container                                                                       | docker:dind                                                                                     |
| `image.pullPolicy`                                       | The pull policy of the controller image                                                                                    | IfNotPresent                                                                                    |
| `metrics.serviceMonitor`                                 | Deploy serviceMonitor kind for for use with prometheus-operator CRDs                                                       | false                                                                                           |
| `metrics.serviceAnnotations`                             | Set annotations for the provisioned metrics service resource                                                               |                                                                                                 |
| `metrics.port`                                           | Set port of metrics service                                                                                                | 8443                                                                                            |
| `metrics.proxy.enabled`                                  | Deploy kube-rbac-proxy container in controller pod                                                                         | true                                                                                            |
| `metrics.proxy.image.repository`                         | The "repository/image" of the kube-proxy container                                                                         | quay.io/brancz/kube-rbac-proxy                                                                  |
| `metrics.proxy.image.tag`                                | The tag of the kube-proxy image to use when pulling the container                                                          | v0.10.0                                                                                         |
| `metrics.serviceMonitorLabels`                           | Set labels to apply to ServiceMonitor resources                                                                            |                                                                                                 |
| `imagePullSecrets`                                       | Specifies the secret to be used when pulling the controller pod containers                                                 |                                                                                                 |
| `fullnameOverride`                                       | Override the full resource names	                                                                                        |                                                                                                 |
| `nameOverride`                                           | Override the resource name prefix	                                                                                        |                                                                                                 |
| `serviceAccount.annotations`                             | Set annotations to the service account                                                                                     |                                                                                                 |
| `serviceAccount.create`                                  | Deploy the controller pod under a service account                                                                          | true                                                                                            |
| `podAnnotations`                                         | Set annotations for the controller pod                                                                                     |                                                                                                 |
| `podLabels`                                              | Set labels for the controller pod                                                                                          |                                                                                                 |
| `serviceAccount.name`                                    | Set the name of the service account                                                                                        |                                                                                                 |
| `securityContext`                                        | Set the security context for each container in the controller pod                                                          |                                                                                                 |
| `podSecurityContext`                                     | Set the security context to controller pod                                                                                 |                                                                                                 |
| `service.annotations`                                    | Set annotations for the provisioned webhook service resource                                                               |                                                                                                 |
| `service.port`                                           | Set controller service ports                                                                                               |                                                                                                 |
| `service.type`                                           | Set controller service type                                                                                                |                                                                                                 |
| `topologySpreadConstraints`                              | Set the controller pod topologySpreadConstraints                                                                           |                                                                                                 |
| `nodeSelector`                                           | Set the controller pod nodeSelector                                                                                        |                                                                                                 |
| `resources`                                              | Set the controller pod resources                                                                                           |                                                                                                 |
| `affinity`                                               | Set the controller pod affinity rules                                                                                      |                                                                                                 |
| `podDisruptionBudget.enabled`                            | Enables a PDB to ensure HA of controller pods                                                                              |      false                                                                                      |
| `podDisruptionBudget.minAvailable`                       | Minimum number of pods that must be available after eviction                                                               |                                                                                                 |
| `podDisruptionBudget.maxUnavailable`                     | Maximum number of pods that can be unavailable after eviction. Kubernetes 1.7+ required.                                   |                                                                                                 |
| `tolerations`                                            | Set the controller pod tolerations                                                                                         |                                                                                                 |
| `env`                                                    | Set environment variables for the controller container                                                                     |                                                                                                 |
| `priorityClassName`                                      | Set the controller pod priorityClassName                                                                                   |                                                                                                 |
| `scope.watchNamespace`                                   | Tells the controller and the github webhook server which namespace to watch if `scope.singleNamespace` is true             | `Release.Namespace` (the default namespace of the helm chart).                                  |
| `scope.singleNamespace`                                  | Limit the controller to watch a single namespace                                                                           | false                                                                                           |
| `certManagerEnabled`                                     | Enable cert-manager. If disabled you must set admissionWebHooks.caBundle and create TLS secrets manually                   | true                                                                                            |
| `runner.statusUpdateHook.enabled`                        | Use custom RBAC for runners (role, role binding and service account), this will enable reporting runner statuses           | false                                                                                           |
| `admissionWebHooks.caBundle`                             | Base64-encoded PEM bundle containing the CA that signed the webhook's serving certificate                                  |                                                                                                 |
| `githubWebhookServer.logLevel`                           | Set the log level of the githubWebhookServer container                                                                     |                                                                                                 |
| `githubWebhookServer.logFormat`                           | Set the log format of the githubWebhookServer controller. Valid options are "text" and "json"                                                                  |   text                                                                                              |
| `githubWebhookServer.replicaCount`                       | Set the number of webhook server pods                                                                                      | 1                                                                                               |
| `githubWebhookServer.useRunnerGroupsVisibility`          | Enable supporting runner groups with custom visibility. This will incur in extra API calls and may blow up your budget. Currently, you also need to set `githubWebhookServer.secret.enabled` to enable this feature. | false |
| `githubWebhookServer.enabled`                            | Deploy the webhook server pod                                                                                              | false                                                                                           |
| `githubWebhookServer.queueLimit`                         | Set the queue size limit in the githubWebhookServer                                                                        |                                                                                                 |
| `githubWebhookServer.secret.enabled`                     | Passes the webhook hook secret to the github-webhook-server                                                                | false                                                                                           |
| `githubWebhookServer.secret.create`                      | Deploy the webhook hook secret                                                                                             | false                                                                                           |
| `githubWebhookServer.secret.name`                        | Set the name of the webhook hook secret                                                                                    | github-webhook-server                                                                           |
| `githubWebhookServer.secret.github_webhook_secret_token` | Set the webhook secret token value                                                                                         |                                                                                                 |
| `githubWebhookServer.imagePullSecrets`                   | Specifies the secret to be used when pulling the githubWebhookServer pod containers                                        |                                                                                                 |
| `githubWebhookServer.nameOverride`                       | Override the resource name prefix	                                                                                        |                                                                                                 |
| `githubWebhookServer.fullnameOverride`                   | Override the full resource names	                                                                                        |                                                                                                 |
| `githubWebhookServer.serviceAccount.create`              | Deploy the githubWebhookServer under a service account                                                                     | true                                                                                            |
| `githubWebhookServer.serviceAccount.annotations`         | Set annotations for the service account                                                                                    |                                                                                                 |
| `githubWebhookServer.serviceAccount.name`                | Set the service account name                                                                                               |                                                                                                 |
| `githubWebhookServer.podAnnotations`                     | Set annotations for the githubWebhookServer pod                                                                            |                                                                                                 |
| `githubWebhookServer.podLabels`                          | Set labels for the githubWebhookServer pod                                                                                 |                                                                                                 |
| `githubWebhookServer.podSecurityContext`                 | Set the security context to githubWebhookServer pod                                                                        |                                                                                                 |
| `githubWebhookServer.securityContext`                    | Set the security context for each container in the githubWebhookServer pod                                                 |                                                                                                 |
| `githubWebhookServer.resources`                          | Set the githubWebhookServer pod resources                                                                                  |                                                                                                 |
| `githubWebhookServer.topologySpreadConstraints`          | Set the githubWebhookServer pod topologySpreadConstraints                                                                  |                                                                                                 |
| `githubWebhookServer.nodeSelector`                       | Set the githubWebhookServer pod nodeSelector                                                                               |                                                                                                 |
| `githubWebhookServer.tolerations`                        | Set the githubWebhookServer pod tolerations                                                                                |                                                                                                 |
| `githubWebhookServer.affinity`                           | Set the githubWebhookServer pod affinity rules                                                                             |                                                                                                 |
| `githubWebhookServer.priorityClassName`                  | Set the githubWebhookServer pod priorityClassName                                                                          |                                                                                                 |
| `githubWebhookServer.service.type`                       | Set githubWebhookServer service type                                                                                       |                                                                                                 |
| `githubWebhookServer.service.ports`                      | Set githubWebhookServer service ports                                                                                      | `[{"port":80, "targetPort:"http", "protocol":"TCP", "name":"http"}]`                            |
| `githubWebhookServer.ingress.enabled`                    | Deploy an ingress kind for the githubWebhookServer                                                                         | false                                                                                           |
| `githubWebhookServer.ingress.annotations`                | Set annotations for the ingress kind                                                                                       |                                                                                                 |
| `githubWebhookServer.ingress.hosts`                      | Set hosts configuration for ingress                                                                                        | `[{"host": "chart-example.local", "paths": []}]`                                                |
| `githubWebhookServer.ingress.tls`                        | Set tls configuration for ingress                                                                                          |                                                                                                 |
| `githubWebhookServer.ingress.ingressClassName`           | Set ingress class name                                                                                                     |                                                                                                 |
| `githubWebhookServer.podDisruptionBudget.enabled`        | Enables a PDB to ensure HA of githubwebhook pods                                                                           | false                                                                                           |
| `githubWebhookServer.podDisruptionBudget.minAvailable`   | Minimum number of pods that must be available after eviction                                                               |                                                                                                 |
| `githubWebhookServer.podDisruptionBudget.maxUnavailable` | Maximum number of pods that can be unavailable after eviction. Kubernetes 1.7+ required.                                   |                                                                                                 |