## Ejercicios LINUX

### 1. Crea mediante comandos de bash la siguiente jerarquía de ficheros y directorios.

```
mkdir -p foo/dummy foo/empty
touch foo/dummy/file2.txt
echo "Me encanta la bash!!" > foo/dummy/file1.txt
```

### 2. Mediante comandos de bash, vuelca el contenido de file1.txt a file2.txt y mueve file2.txt a la carpeta empty.

```
cd foo/dummy
cat file1.txt > file2.txt
mv file2.txt ../empty/file2.txt
```

### 3. Crear un script de bash que agrupe los pasos de los ejercicios anteriores y además permita establecer el texto de file1.txt alimentándose como parámetro al invocarlo.

#### Crear un fichero para el script y entrar para editar

```
touch script_3.sh
vi script_3.sh
```

#### Contenido del fichero con script

```
mkdir -p foo/dummy foo/empty
touch foo/dummy/file2.txt

if [ -n "$1" ]; then
echo "$1" > foo/dummy/file1.txt
else
echo "Que me gusta la bash!!!!" > foo/dummy/file1.txt
fi

cd foo/dummy
cat file1.txt > file2.txt
mv file2.txt ../empty/file2.txt
```

#### Comando para ejecutar el script

```
bash script_3.sh
```

### 4. Crea un script de bash que descargue el contenido de una página web a un fichero y busque en dicho fichero una palabra dada como parámetro al invocar el script

#### Crear un fichero para el scripty entrar para editar

```
touch script_4.sh
vi script_4.sh
```

#### Contenido del fichero con script

```
COUNT_SEARCH_RESULT=$(curl -o ./bbc-response.txt https://www.bbc.com | grep -c $1 bbc-response.txt)
LINE_OF_FIRST_OCCURRENCY=$(grep -n -m 1 $1 bbc-response.txt |cut -f1 -d:)

if [ $COUNT_SEARCH_RESULT -ne 0 ]; then
echo "La palabra $1 aparece $COUNT_SEARCH_RESULT veces"
echo "Aparece por primera vez en la linea $LINE_OF_FIRST_OCCURRENCY"
else
echo "No se ha encontrado la palabra $1"
fi
```

### 5. OPCIONAL - Modifica el ejercicio anterior de forma que la URL de la página web se pase por parámetro y también verifique que la llamada al script sea correcta

#### Crear un fichero para el scripty entrar para editar

```
touch script_5.sh
vi script_5.sh
```

#### Contenido del fichero con script

```
if [ "$#" -lt 2 ]; then
echo "Se necesitan dos parámetros para ejecutar este script"
exit
fi

if [ "$#" -gt 2 ]; then
echo "Se necesitan únicamente dos parámetros para ejecutar este script"
exit
fi

COUNT_SEARCH_RESULT=$(curl -o ./response.txt $1 | grep -c $2 response.txt)
LINE_OF_FIRST_OCCURRENCY=$(grep -n -m 1 $2 response.txt |cut -f1 -d:)

if [ $COUNT_SEARCH_RESULT -ne 0 ]; then
echo "La palabra $2 aparece $COUNT_SEARCH_RESULT vez"
echo "Aparece únicamente en la linea $LINE_OF_FIRST_OCCURRENCY"
elif [ $COUNT_SEARCH_RESULT -eq 1]; then
echo "La palabra $2 aparece $COUNT_SEARCH_RESULT veces"
echo "Aparece por primera vez en la linea $LINE_OF_FIRST_OCCURRENCY"
else
echo "No se ha encontrado la palabra $2"
fi
```
