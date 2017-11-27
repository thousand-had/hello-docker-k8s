# kubeadm for Vagrant

## Vagrant VM Installation
- `vagrant up`

## Master Initialization
- `sudo kubeadm reset`
- `sudo kubeadm init`
- `sudo swapoff -a`
- `sudo kubeadm init --pod-network-cidr=88.88.88.0/16 --apiserver-advertise-address=88.88.88.2`
- `mkdir -p $HOME/.kube`
- `sudo cp -f /etc/kubernetes/admin.conf $HOME/.kube/config`
- `sudo chown $(id -u):$(id -g) $HOME/.kube/config`

- `kubectl apply -f http://docs.projectcalico.org/v2.4/getting-started/kubernetes/installation/hosted/kubeadm/1.6/calico.yaml`
- `kubectl delete deployment kube-dns --namespace=kube-system`
- `kubectl apply -f kubernetes/templates/kube-dns.yaml`
- `kubectl taint nodes --all node-role.kubernetes.io/master-`
- `kubectl proxy&`
- `kubectl get po --namespace=kube-system`

## Node Initialization
- `kubeadm join --token fdaae4.96ec9aa698065a40 88.88.88.2:6443 --discovery-token-ca-cert-hash sha256:04270543e0398565877970b72da4026a93b31213467226e63d37d05aee000710`

## Test
- `kubectl get nodes`