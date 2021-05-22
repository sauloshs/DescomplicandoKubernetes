# ***Portas que devemos nos preocupar***

## ***Kubernetes***

- Master  kube-apiserver
  - 6443 TCP
- etcd server API
  - 2379-2380 TCP
- Kubelet API
  - 10250 TCP
- kube-scheduler
  - 10251 TCP
- kube-controller-manager
  - 10252 TCP
- Kubelet API Read-only
  - 10255 TCP
- TCP WORKER Kubelet API
  - 10250 TCP
- NodePort Services
  - 30000-32767 TCP

