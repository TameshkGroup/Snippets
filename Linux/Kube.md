To fix this error
```
network is not ready: container runtime network not ready: NetworkReady=false reason:NetworkPluginNotReady message:docker: network plugin is not ready: cni config uninitialized
```

firstly install flannel and then:

/run/flannel/subnet.env

```bash
FLANNEL_NETWORK=10.244.0.0/16
FLANNEL_SUBNET=10.244.0.1/24
FLANNEL_MTU=1450
FLANNEL_IPMASQ=true
```
## Renew the certificates
```bash
kubeadm certs renew all
```
Then it warns:
> Done renewing certificates. You must restart the kube-apiserver, kube-controller-manager, kube-scheduler and etcd, so that they can use the new certificates.

1. Update your `.kube/config`
2. Connet to server with the new config 
3. Restart these pods by simply deleting them.

- if you want to update server kube config:
  ```bash
  cat /etc/kubernetes/admin.conf > $HOME/.kube/config
  ```

## openlens extension to view logs

`@alebcay/openlens-node-pod-menu`
