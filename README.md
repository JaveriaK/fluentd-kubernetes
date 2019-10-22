# Fluentd-Kafka Image and Daemonset for Kubernetes

### Docker Image
  
- The `docker-image` files are based off of the upstream `fluentd-kubernetes-daemonset` source here (master is currently on v1.4): https://github.com/fluent/fluentd-kubernetes-daemonset

- A pre-built image can be pulled from `jvkhan/fluentd:v1.4-kafka`

- Some of the conf files baked into the image, present under `docker-image/conf`, are also loaded into the running daemonset as configMaps, so a new image need not be built just for conf changes.

### Kubernetes Daemonset

- This contains manifests for a Daemonset, RBAC roles, ConfigMaps and a dummy service (for liveness checks only); and can be applied with:

```
kubectl apply -f kubernetes/fluentd-rbac.yaml
kubectl apply -f kubernetes/fluentd-daemonset-svc.yaml
kubectl apply -f kubernetes/fluentd-config.yaml
kubectl apply -f kubernetes/fluentd-daemonset-kafka.yaml
```
