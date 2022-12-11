### 1. Crear el escenario, aplicando el namespace

```
kubectl apply -f ns.yml
```

### 2. Aplicar el namespace creado como actual del contexto

```
kubectl config set-context --current --namespace=monolithinmem
```

### 3. Aplicar servicio

```
kubectl apply -f svc.yml
```

### 4. Aplicar deployment 
#### (la imagen de la app hemos construido `docker build -t romandorosh/lc-todo-monolith . ` y subimos `docker push romandorosh/lc-todo-monolith` al DockerHub previamente)

```
kubectl apply -f deploy.yml
```

### 5. Usando minikube, dejar coriendo tunnel en una pestaña separada del terminal

```
minikube tunnel
```

### 6. Comprobar IP externo del servicio que hemos creado

```
kubectl get svc
```

### 7. Abrir navegador y sustituir por IP externo de nuestro servicio (segun configuracion se utiliza el puerto 3001)
```
http://REPLACE_WITH_EXTERNAL_IP:3001
```