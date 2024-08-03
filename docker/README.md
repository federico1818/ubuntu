# Laravel

## Crear un proyecto desde cero

1. Nombrar proyecto

```sh
unset PROJECT_NAME && export PROJECT_NAME="my-project"
```

2. Crear carpeta

```sh
mkdir ~/workspace/projects/$PROJECT_NAME
```

3. Copiar carpeta de docker

```sh
cp -R ./docker/laravel/ ~/workspace/projects/$PROJECT_NAME/$PROJECT_NAME-docker
```

4. Editar el archivo ```.env```

5. Editar el archivo ```sites/enabled/site.conf```

6. Levantar entorno

```sh
cd ~/workspace/projects/$PROJECT_NAME/$PROJECT_NAME-docker && docker-compose up -d
```

7. Crear proyecto

```sh
docker run --rm --interactive --tty \
    --volume ~/workspace/projects/$PROJECT_NAME:/app \
    --user $(id -u):$(id -g) \
    composer create-project laravel/laravel=11.1.4 $PROJECT_NAME-laravel
```

# Angular

1. Nombrar proyecto

```sh
unset PROJECT_NAME && export PROJECT_NAME="my-project"
```

2. Crear carpeta

```sh
mkdir -p ~/workspace/projects/$PROJECT_NAME/$PROJECT_NAME-angular
```

3. Copiar carpeta de docker

```sh
cp -R ./docker/angular-18-1-3/ ~/workspace/projects/$PROJECT_NAME/$PROJECT_NAME-angular/docker
```

4. Configurar variables de entorno

```sh
unset GIT_USER_NAME && export GIT_USER_NAME=$(git config user.name)
unset GIT_USER_EMAIL && export GIT_USER_EMAIL=$(git config user.email)
```

5. Crear image

```sh
docker build \
-t node-angular:18-1-3 \
--build-arg name="${GIT_USER_NAME}" \
--build-arg email="${GIT_USER_EMAIL}" \
~/workspace/projects/$PROJECT_NAME/$PROJECT_NAME-angular/docker/node-20-16-0
```

6. Editar el archivo ```.env```


5. a. Ejecutar entorno

```sh
docker-compose -f ~/workspace/projects/$PROJECT_NAME/$PROJECT_NAME-angular/docker/docker-compose.yml -p node-angular up -d
```

5. b. Detener entorno

```sh
docker-compose -f ~/workspace/projects/$PROJECT_NAME/$PROJECT_NAME-angular/docker/docker-compose.yml -p node-angular down
```

6. Crear proyecto

```sh
docker exec -it \
    node-angular ng new $PROJECT_NAME-angular \
    --directory=$PROJECT_NAME/$PROJECT_NAME-angular \
    --routing \
    --style=scss \
    --ssr=false \
    --interactive=false
```

7. Ejecutar aplicación

```sh
docker exec -it \
    node-angular ng serve --host 0.0.0.0
```