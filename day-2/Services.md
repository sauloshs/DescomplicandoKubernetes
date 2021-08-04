# ***Trabalhando com Services***

## ***Criando um Service a partir de um arquivo***

​	Com esse comando podemos criar um service a partir de um arquivo .yaml

```shell
 kubectl get service <nome_do_service> -o yaml > meu_primeiro_service.yaml
```

​	Exemplo de arquivo de service do tipo NodePort:

```yaml
apiVersion: v1
kind: Service
metadata:
  labels:
    app: referencia
  name: referencia
  namespace: default
spec:
  externalTrafficPolicy: Cluster
  ipFamilies:
  - IPv4
  ipFamilyPolicy: SingleStack
  ports:
  - nodePort: 32221
    port: 8080
    protocol: TCP
    targetPort: 8080
  selector:
    app: referencia
  sessionAffinity: None
  type: NodePort
```

​	Exemplo de arquivo de service do tipo LoadBalancer:
```yaml
apiVersion: v1
kind: Service
metadata:
  labels:
    run: nginx
  name: nginx-loadbalancer
  namespace: default
spec:
  externalTrafficPolicy: Cluster
  ports:
  - nodePort: 32548
    port: 80
    protocol: TCP
    targetPort: 80
  selector:
    run: nginx
  sessionAffinity: None
  type: LoadBalancer
```

## ***Linstando endpoints do deployment***

​	Os endpoints do deployments nada mais é do que o IP dos pods e sua respectiva porta 

```shell
kubectl get endpoints
```

