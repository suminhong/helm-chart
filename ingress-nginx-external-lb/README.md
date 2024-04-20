# ingress-nginx

base: [ingress-nginx/ingress-nginx/4.10.0](https://artifacthub.io/packages/helm/ingress-nginx/ingress-nginx/4.10.0)

different: ingress-nginx를 NodePort 타입으로 사용하는 경우, 별도로 프로비저닝된 AWS LB와 연동 가능
(LB의 DNS 주소와 Target Group의 ARN 필요)

## Requirements

Kubernetes: `>=1.20.0-0`

## Get Repo Info

```console
helm repo add suminhong https://suminhong.github.io/helm-chart
helm repo update
```

## Install Chart

**Important:** only helm3 is supported

```console
helm install [RELEASE_NAME] suminhong/ingress-nginx-external-lb
```

The command deploys ingress-nginx on the Kubernetes cluster in the default configuration.

## Example
```console
controller:
  extraArgs:
    # for external-dns
    publish-status-address: <dns-to-lb>
  service:
    type: NodePort
    targetPorts:
      http: http
      https: http
    nodePorts:
      http: 30004
      https: null
    targetGroupBinding:
      create: true
      arnMapping:
        http: <arn-to-targetGroup>
        https: <arn-to-targetGroup>
```
