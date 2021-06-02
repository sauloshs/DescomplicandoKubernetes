# ***Instalando o Kubernetes***

​	Para realizar a instalação do Kubernetes é necessário alguns pre requisitos;

## ***Instalação do Docker***

```shell
curl -fsSL https://get.docker.com | bash
```

## ***Configurações necessárias no host***

​	No arquivo /etc/docker/daemon.json

```json
{
	"exec-opts": ["native.cgroupdriver=systemd"],
	"log-driver": "json-file",
	"log-opts": {
		"max-size": "100m"
	},
	"storage-driver": "overlay2"
}
```

​	Criar o diretório "docker,service.d"

```shell
mkdir -p /etc/systemd/system/docker.service.d
```

 	Após esses passos devemos reiniciar o serviço do Docker

```shell
systemctl daemon-reload

systemctl restart docker

docker info | grep -i cgroup # conferindo se o Docker foi iniciar no systemd
```

## ***Instalando o Kubernetes***

### ***Adicionando ao repositório***

```shell
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
```

```shell
echo "deb http://apt.kubernetes.io/ kubernetes-xenial main" > /etc/apt/sources.list.d/kubernetes.list
```

```shell
apt-get update
apt-get install -y kubeadm kubelet kubectl
```

## ***Configuração Inicial***

​	No nó máster devemos realizar os seguintes procedimentos:

```shell
kubeadm config images pull
```

### ***Inicializando o cluster***

```shell
kubeadm init	#Caso acontece erro de swap usar o comando "swapoff -a"
```

​	Após a inicialização:

```shell
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown $(id -u):$(id -g) $HOME/.kube/config
```

### ***Subindo módulos do Kernel necessários***

```shell
modprobe br_netfilter ip_vs_rr ip_vs_wrr ip_vs_sh nf_conntrack_ipv4 ip_vs
```

### ***Criando os Pods Networks***

```shell
kubectl apply -f "https://cloud.weave.works/k8s/net?k8s-version=$(kubectl version | base64 | tr -d '\n')"
```

### ***Adicionando outros nós ao clustes***

​	No exemplo a baixa a saída do comando kubeadm init retornou o seguinte token:

```shell
kubeadm join 192.168.17.20:6443 --token 6213fm.do6crc2oyuv4grvi \
        --discovery-token-ca-cert-hash sha256:6ecb398ea4ce39d9480dd006511e17605a58243ca42316633c7260e1646a1ded
```

