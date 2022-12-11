### 1. Crear el escenario, aplicando el namespace

```
kubectl apply -f ns.yml
```

### 2. Aplicar el namespace creado como actual del contexto

```
kubectl config set-context --current --namespace=monolith
```

### 3. Aplicar servicio para todo-app

```
kubectl apply -f svc-app.yml
```

### 4. Aplicar servicio para bd

```
kubectl apply -f svc-bd.yml
```

### 5. Aplicar storage class

```
kubectl apply -f sc.yml
```

### 6. Aplicar persistent volume

```
kubectl apply -f pv.yml
```

### 7. Aplicar persistent volume claim

```
kubectl apply -f pvc.yml
```

### 8. Aplicar config map para app

```
kubectl apply -f cm-app.yml
```

### 9. Aplicar config map para bd

```
kubectl apply -f cm-bd.yml
```

### 10. Aplicar statefulset

```
kubectl apply -f ss.yml
```

### 11. Aplicar deployment
#### (la imagen de la app hemos construido `docker build -t romandorosh/lc-todo-monolith-01 . ` y subimos `docker push romandorosh/lc-todo-monolith-01` al DockerHub previamente)

```
kubectl apply -f deploy.yml
```

### 12. Usando minikube, dejar coriendo tunnel en una pestaña separada del terminal

```
minikube tunnel
```

### 13. Comprobar IP externo del servicio de app (todo-app-loadbalancer) que hemos creado con `svc-app.yml`

```
kubectl get svc
```

### 14. Abrir navegador y sustituir por IP externo de nuestro servicio (segun configuracion se utiliza el puerto 3000)
```
http://REPLACE_WITH_EXTERNAL_IP:3000
```