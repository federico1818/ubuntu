# Laravel

## Nombrar proyecto

```sh
unset PROJECT_NAME && export PROJECT_NAME="my-project"
```

## Crear carpeta

```sh
mkdir ~/workspace/projects/$PROJECT_NAME
```

## Copiar carpeta de docker

```sh
cp -R ./docker/laravel/ ~/workspace/projects/$PROJECT_NAME/$PROJECT_NAME-docker
```

## Levantar entorno

```sh
cd ~/workspace/projects/$PROJECT_NAME/$PROJECT_NAME-docker && docker-compose up -d
```

## Crear proyecto

```sh
docker run --rm --interactive --tty \
    --volume ~/workspace/projects/$PROJECT_NAME:/app \
    --user $(id -u):$(id -g) \
    composer create-project laravel/laravel=11.1.4 $PROJECT_NAME-laravel
```