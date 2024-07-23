# Laravel

## Nombrar proyecto

```sh
unset PROJECT_NAME && export PROJECT_NAME="my-project"
```

## Crear carpeta

```sh
mkdir ~/workspace/laravel/$PROJECT_NAME
```

## Copiar carpeta de docker

```sh
cp -R ./docker/laravel/ ~/workspace/laravel/$PROJECT_NAME/docker
```

## Levantar entorno

```sh
cd ~/workspace/laravel/$PROJECT_NAME/docker && docker-compose up -d
```