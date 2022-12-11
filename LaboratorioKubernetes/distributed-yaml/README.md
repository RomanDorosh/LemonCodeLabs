### 1. Crear el escenario, aplicando el namespace

```
kubectl apply -f ns.yml
```

### 2. Aplicar el namespace creado como actual del contexto

```
kubectl config set-context --current --namespace=distributed
```

### 3. Aplicar servicio para front

```
kubectl apply -f svc-front.yml
```

### 4. Aplicar servicio para api

```
kubectl apply -f svc-api.yml
```

### 5. Aplicar deployment del front
#### (la imagen del front hemos construido `docker build -t romandorosh/lc-todo-front-distributed . ` y subimos `docker push romandorosh/lc-todo-front-distributed` al DockerHub previamente)

```
kubectl apply -f deploy_front.yml
```

### 6. Aplicar deployment de la api
#### (la imagen de la api hemos construido `docker build -t romandorosh/lc-todo-api-distributed . ` y subimos `docker push romandorosh/lc-todo-api-distributed` al DockerHub previamente)

```
kubectl apply -f deploy_api.yml
```

### 4. Aplicar ingress
```
kubectl apply -f ingress.yml   
```

