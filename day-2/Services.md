# ***Trabalhando com Services***

## ***Criando um Service a partir de um arquivo***

​	Com esse comando podemos criar um service a partir de um arquivo .yaml

```shell
 kubectl get service <nome_do_service> -o yaml > meu_primeiro_service.yaml
```

​	Exemplo de arquivo de service:

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

## ***Linstando endpoints do deployment***

​	Os endpoints do deployments nada mais é do que o IP dos pods e sua respectiva porta 

```shell
kubectl get endpoints
```

