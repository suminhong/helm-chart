# Slack Emoji Maker Helm Chart

A Helm chart for deploying the Slack Emoji Maker web application.

## Prerequisites

- Kubernetes 1.19+
- Helm 3.0+

## Installing the Chart

```bash
helm repo add slack-emoji-maker https://raw.githubusercontent.com/honglab/helm-charts/main
helm install emoji-maker slack-emoji-maker/slack-emoji-maker
```

## Configuration

The following table lists the configurable parameters of the slack-emoji-maker chart and their default values.

| Parameter | Description | Default |
|-----------|-------------|---------|
| `replicaCount` | Number of replicas | `1` |
| `image.repository` | Image repository | `honglab/slack-emoji-maker` |
| `image.tag` | Image tag | `v0.0.1` |
| `image.pullPolicy` | Image pull policy | `IfNotPresent` |
| `service.type` | Service type | `ClusterIP` |
| `service.port` | Service port | `80` |
| `service.targetPort` | Service target port | `5173` |
| `ingress.enabled` | Enable ingress | `false` |
| `resources.limits.cpu` | CPU limit | `200m` |
| `resources.limits.memory` | Memory limit | `256Mi` |
| `resources.requests.cpu` | CPU request | `100m` |
| `resources.requests.memory` | Memory request | `128Mi` |

## Example Usage

### Basic Installation
```bash
helm install emoji-maker slack-emoji-maker/slack-emoji-maker
```

### Custom Configuration
```bash
helm install emoji-maker slack-emoji-maker/slack-emoji-maker \
  --set service.type=LoadBalancer \
  --set ingress.enabled=true \
  --set ingress.hosts[0].host=emoji.example.com
```
