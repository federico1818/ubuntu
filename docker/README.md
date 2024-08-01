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