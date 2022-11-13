# Ejercicio 1

### Creamos la red llamada "lemoncode-challenge"

```
docker network create lemoncode-challenge
```

### Creamos el volumen llamado "mongo_data"

```
docker volume create mongo_data
```

### Arrancamos el contenedor desde la imagen del mongo, indicando la red, volumen y variables del entorno

```
docker run --network lemoncode-challenge --name some-mongo \
    -p 27017:27017 \
    -v mongo_data:/data/db \
    -e MONGO_INITDB_ROOT_USERNAME=root \
    -e MONGO_INITDB_ROOT_PASSWORD=root \
    -d mongo:latest
```

### Creamos el fichero "Dockerfile" dentro de la carpeta "backend" con el siguente contenido:

```
FROM node:16-alpine

WORKDIR /app

COPY ["package.json", "package-lock.json*", "./"]

RUN npm install

COPY . .

CMD npm start
```

### Creamos la imagen del backend (desde carpeta "backend")

```
docker build -t topics-api .
```

### Arrancamos el contenedor desde la imagen del backend que hemos creado, indicando la red y variables del entorno

```
docker run --network lemoncode-challenge --name topics-api \
    -e DATABASE_URL=mongodb://root:root@some-mongo:27017 \
    -e DATABASE_NAME=TopicstoreDb \
    -e HOST=topics-api \
    -d topics-api
```

### Creamos el fichero "Dockerfile" dentro de la carpeta "frontend" con el siguente contenido:

```
FROM node:16-alpine

WORKDIR /app

COPY ["package.json", "package-lock.json*", "./"]

RUN npm install

COPY . .

EXPOSE 3000

CMD npm start
```

### Creamos la imagen del frontend (desde carpeta "frontend")

```
docker build -t frontend .
```

### Arrancamos el contenedor desde la imagen del frontend que hemos creado, indicando la red, puertos y variables del entorno

```
docker run --network lemoncode-challenge --name frontend \
    -e API_URI=http://topics-api:5000/api/topics \
    -p 8080:3000 \
    -d frontend
```

#Ejercicio 2

## Para crear las imagenes desde compose fichero "docker-compose.yml" en el mismo directorio y levantar con ellas los contenedores

```
docker compose up
```

## Para parar todos contenedores levantados con el fichero compose en el mismo directorio, sin eliminarlos

```
docker compose stop
```

## Para parar y eliminar todos contenedores y las redes levantados con el fichero compose en el mismo directorio

```
docker compose down
```
