# Example 01 - Argo Rollouts - Canary Setup for Internal services

This is an demo to show Argo Rollout feature for internal services (applications that do not have a public endpoint and is used by other applications via service name).

Reference: https://github.com/argoproj/argo-rollouts/issues/617

## Installation

### Install argo rollouts controller
https://argoproj.github.io/argo-rollouts/installation.html#controller-installation

### Install kubectl argo plugin
https://argoproj.github.io/argo-rollouts/installation.html#kubectl-plugin-installation

### Setup

1. Apply yaml files

```bash
$ kubectl apply -f rollout.yaml
$ kubectl apply -f services.yaml
$ kubectl apply -f virtualsvc.yaml
$ kubectl apply -f nginx.yaml
```

2. Wait till pods hae started & then check rollout

```bash
$ kubectl argo rollouts get rollout rollouts-demo
```

3. Create canary deployment
```bash
  kubectl argo rollouts set image rollouts-demo rollouts-demo=argoproj/rollouts-demo:purple
$ kubectl argo rollouts set image rollouts-demo rollouts-demo=gcr.io/fetch-ai-sandbox/argo-test:canary
```

4. Enter into nginx container
```bash
$ apt-get update && apt-get install -y curl

$ curl http://rollouts-demo
```






kubectl patch cm argo-rollouts-notification-configmap -n argocd --type merge -p '{"data": {"service.email.gmail": "{ username: tempmail436@gmail.com, password: tempmailpassword, host: smtp.gmail.com, port: 465, from: tempmail436@gmail.com }",
"service.slack": "{ apiURL: <url>, token: xoxb-2219249599776-2228900099952-LoW9o6AN2C3EISnpCdW0VVGC, username: username, icon: icon }"}}'
