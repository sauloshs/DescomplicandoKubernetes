# ***Trabalhando com Minikube***

## ***Instalação Kubectl***

​	Antes de instalar o Minikube, precisamos realizar a instalação do Kubectl:

### ***Linux***

```shell
curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl

chmod +x kubectl && mv kubectl /usr/local/bin/
```

### ***Mac OS***

```shell
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/darwin/amd64/kubectl

chmod +x kubectl && mv kubectl /usr/local/bin
```

### ***Windows***

```powershell
curl -Lo https://storage.googleapis.com/kubernetes-release/release/v1.13.7/bin/windows/amd64/kubectl.exe

Se você utiliza o PSGallery:

Install-Script -Name install-kubectl -Scope CurrentUser -Force    
install-kubectl.ps1 [-DownloadLocation <path>]
```

## ***Instalação MInikube***

```
https://kubernetes.io/docs/tasks/tools/install-minikube/
```

### ***Linux***

```shell
# curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 \ && chmod +x minikube
# sudo cp minikube /usr/local/bin && rm minikube
```

### ***Mac OS***

```shell
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64 \ && chmod +x minikube
sudo cp minikube /usr/local/bin && rm minikube
```

### ***Windows***

```
https://storage.googleapis.com/minikube/releases/v1.1.1/minikube-windows-amd64.exe
```

## ***Comandos básicos Minikube***

### ***Iniciando***

```shell
minikube start
```

### ***Parando***

```shell
minikube stop
```

### ***Listando nodes***

```shell
kubectl get nodes	
```

### ***Lista IP da máquina virtual do Minikube***

```shell
minikube ip	
```

### ***Conectar a máquina do Minikube***

```shell
minikube ssh 
```

### ***Acessar painel Minikube***

```shell
minikube dashboard
```

### ***Verificando os logs***

```shell
minikube logs
```

### ***Deletar máquina MInikube***

```shell
minikube delete
```

