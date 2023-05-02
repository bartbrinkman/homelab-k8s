## example kubeadm (assuming single control plane and flannel)

```
kubeadm init --pod-network-cidr=10.244.0.0/16
```
```
kubectl apply -f https://raw.githubusercontent.com/flannel-io/flannel/master/Documentation/kube-flannel.yml
```

## Argo CD

This cluster is based on Argo CD's app-of-apps pattern, which can be set up using the Quick Start in the [documentation](https://argo-cd.readthedocs.io/en/stable/).

## kube-prometheus-stack

- The CRD's are too large and must be applied manually. They are skipped by ArgoCD while syncing (`skipCrds: true`).

# using DirectPV

- the app-of-apps app for MinIO also sets up DirectPV, but will require additional [installation instructions](https://github.com/minio/directpv/blob/master/docs/installation.md) that might not be useful with GitOps, such as discovering drives on nodes.

## Use all nodes

```
kubectl taint nodes --all node-role.kubernetes.io/control-plane:NoSchedule-
```
