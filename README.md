# Instalar GIT

[Link](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

```sh
sudo apt-get install git-all
```

Verificar instalación

```sh
git --version
```

# Configurar GITHUB

Generar SSH Key

```sh
ssh-keygen -t ed25519 -C "federico1818@gmail.com"
```

```sh
eval "$(ssh-agent -s)"
```

```sh
ssh-add ~/.ssh/id_ed25519
```

Ir a [Settings / Keys](https://github.com/settings/keys) y copiar el contenido:

```sh
cat .ssh/id_ed25519.pub
```

# Configurar VSCode

Copiar en la carpeta ```~/.config/Code/User/``` los archivos:
* ```keybindings.json``` 
* ```settings.json```