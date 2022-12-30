## Ejercios Jenkins
 
### 1. CI/CD de una Java + Gradle

 #### 1.1 Construimos imágen de Docker y arrancamos el contenedor con el Dockerfile dentro de la carpeta `jenkins-resources`
 
 #### 1.2 Abrimos Jenkins en navegador, creamos nueva tarea de pipeline, indicando nuestro repositorio y el `Script Path` para el jenkinsFile que en nuestro caso seria `LaboratorioJenkins/1-exercise-Jenkinsfile/Jenkinsfile`
 
 #### 1.3 Guardamos los cambios y construimos el pipeline, el log esta en [Log de Ejercicio 1](https://github.com/RomanDorosh/LemonCodeLabs/blob/main/LaboratorioJenkins/screen-shots/exercise1.txt) y resultado visual deberia de ser: 
 
![Screenshot of first exercise](https://github.com/RomanDorosh/LemonCodeLabs/blob/main/LaboratorioJenkins/screen-shots/exercise1.png)
       


### 2. Modificar la pipeline para que utilice la imagen Docker de Gradle como build runner

#### 2.1 Construimos imágenes de Docker y arrancamos los contenedores con el `docker compose up` dentro de la carpeta `jenkins-resources`
 
 #### 2.2 Abrimos Jenkins en navegador, creamos nueva tarea de pipeline, indicando nuestro repositorio y el `Script Path` para el jenkinsFile que en nuestro caso seria `LaboratorioJenkins/2-exercise-Jenkinsfile/Jenkinsfile`
 
 #### 2.3 Guardamos los cambios y construimos el pipeline, el log esta en [Log de Ejercicio 2](https://github.com/RomanDorosh/LemonCodeLabs/blob/main/LaboratorioJenkins/screen-shots/exercise2.txt)
 
