# Workshop

## Deliver 15-Factor Applications on Kubernetes with Spring Boot

There is a lot of pre-baked content here, but my goal is for you to learn, so, please ask questions.  I will not be racing to get through everything, I will happily go in whatever direction the workshop needs to go, to provide the most value to you.

## Prerequisites

- Docker running locally
- Kubernetes
- Helm
- Java 17 with GraalVM
- `curl`, `wget` or `httpie`
- [Knative CLI](https://knative.dev/docs/client/install-kn/) (Optional)
- [kubectx + kubens](https://github.com/ahmetb/kubectx) (Optional)
- [k9s](https://k9scli.io/) (Optional)

## Kubernetes

If you have a Kubernetes cluster to use, that is fantastic!

If you need access to an ephemeral Kubernetes cluster, you can use [Tanzu Academy](https://tanzu.academy/).

You can also install Kubernetes with KNative using the [Knative Quickstart Plugin](https://knative.dev/docs/install/quickstart-install/)

I like to use `Docker Desktop` on my laptop, because it has buttons for me to enable/disable/reset Kubernetes. When it's running, there are 9 images running in the `kube-system` namespace.  Those Kubernetes system images can optionally be shown/hidden from the Docker Desktop UI.

```bash
kubectl get pod
```
>No resources found in apps namespace.

## Java 17 with GraalVM

I'm a big fan of [SDKMAN!](https://sdkman.io/), so I recommend using that to install GraalVM.

```bash
sdk install java 17.0.8-graalce
sdk use java 17.0.8-graalce
java -version
```
>openjdk version "17.0.8" 2023-07-18\
>OpenJDK Runtime Environment GraalVM CE 17.0.8+7.1 (build 17.0.8+7-jvmci-23.0-b15)\
>OpenJDK 64-Bit Server VM GraalVM CE 17.0.8+7.1 (build 17.0.8+7-jvmci-23.0-b15, mixed mode, sharing)


## Knative

If you are using the Developer Sandbox from Tanzu Academy, you have Knative installed already.

If you are running your own Kubernetes cluster, you can install Knative with the following commands:

```bash
kubectl apply -f https://github.com/knative/operator/releases/download/knative-v1.11.4/operator.yaml
```

## Platform Provided Services

```bash
kn service create zipkin --image openzipkin/zipkin:latest --port 9411 --scale-min 1 -n springkubed-io
kn service create vault --image hashicorp/vault:latest --port 8200 --scale-min 1 -n springkubed-io
helm repo add hashicorp https://helm.releases.hashicorp.com
helm install vault hashicorp/vault
```

[Prometheus & Grafana](https://tanzu.vmware.com/developer/guides/observability-prometheus-grafana-p1/)

[Vault](https://github.com/hashicorp/vault-helm)

- http://prometheus-kube-prometheus-prometheus.default.svc.cluster.local:9090
- http://vault.default.svc.cluster.local:8200

## Spring Cloud Gateway
## Spring Authorization Server
## Oauth 2.0 Client and Resource Server