# ***Primeiros passos Kubernetes***

****

​	Por padrão o nó máster não recebe contêineres.

## ***Habilitando o Completion***

​	Será necessario validar se o "bash-completion" já esta instalado nó seu sistema operacional.

```shell
apt-get install -y bash-completion
```

### ***Habilitando***

```shell
kubectl completion bash > /etc/bash_completion.d/kubectl
```
​	Forçando o carregamento do bash, sem a necessidade de reiniciar o bash.

```shell
source <(kubectl completion bash)
```
## ***Comandos Kubertentes (Nodes)***

### ***Listando nodes***

```shell
kubectl get nodes	
```

### ***Exibindo detalhes dos nodes***

```shell
kubectl describe nodes <nome_do_node>
```

### ***Recuperando token do node***

​	Usado para adicionar novo nodes ao cluster.

```shell
kubeadm token create --print-join-command
```

### ***Exibindo detalhes do pods***

```shell
kubectl describe pods -n kube-system <nome_do_pod> #kube-system é o seu namespace
```

### ***Listando pods***

```shell
kubectl get pods #Quando não especidicado namespace o padrão é usado.
```

​	Para listar todos os NameSpaces.

```shell
kubectl get pods --all-namespaces
```

​	Para verificar em qual nó do cluster ele esta rodando adiciona o parâmetro  "-o wide"

```shell
kubectl get pods --all-namespaces -o wide
```

​	Para ter uma saída do objeto em formato yaml usamos o parâmetro "-o yaml."

```shell
kubectl get pods <nome_do_pod> -o yaml
```

### ***Listando Namespaces***

```shell
kubectl get namespaces
```

### ***Criando Namespace***

```shell
kubectl create namespace <nome_do_namespace>
```

### ***Listando mais de um tipo de informação***

```shell
kubectl get pods,services,endpoints
```

## ***Criando meu Pod***

​	Nas versões mais recentes esse comando não cria o deploy.

```shell
kubectl run nginx --image=nginx 
```

### ***Criando patravésavês de um arquivo***

```shell
kubectl create -f meu_primeiro_pod.yaml
```

### ***Deletando pod através de um arquivo***

```shell
kubectl delete -f meu_primeiro_pod.yaml
```

### ***Criando um arquivo template de pod***

​	Com o comando a baixo usando o parâmetro "--dry=client" ele não cria o pod.

```shell
kubectl run nginx --image=nginx --dry=client
```

​	Após o procedimento acima redirecionamos a saida do comando "-o ymal" para um arquivo.

```shell
kubectl run nginx --image=nginx --dry=client -o yaml > meu_segundo_pod.yaml
```

## ***Expondo o pod fora do cluster (Service)***

​	Verificar se a porta foi exposta no momento da criação do pod.

```shell
kubectl expose pod nginx
```

​	No exemplo a cima ele criou um service do tipo ClusterIP que só tem acesso de dentro do cluster.

### ***Listando os services***

```shell
kubectl get service
```

### ***Exibindo detalhes do services***

```shell
kubectl descibe services nginx
```

### ***Listando endpoints***

```shell
kubectl get endpoints 
```

### ***Editando um services***

```shell
kubectl edit service nginx
```

​	Podemos mudar o seu tipo com esse comando, para NodePort exemplo.

