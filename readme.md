## example kubeadm (assuming single control plane and flannel)

```
kubeadm init --pod-network-cidr=10.244.0.0/16
```
```
kubectl apply -f https://raw.githubusercontent.com/flannel-io/flannel/master/Documentation/kube-flannel.yml
```


## kube-prometheus-stack

- The CRD's are too large and must be applied manually. They are skipped by ArgoCD while syncing (`skipCrds: true`).
