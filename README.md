# Notas Kali Linux 
______________________

En este README pretendo abarcar las configuraciones basicas necesarias de Kali Linux.

Video de referencia:
[BLACKMANTISECURITY](https://youtu.be/6UnvG7ulAZY)


## PIP

Pip es es un gestor de paquetes de Python.

```
sudo apt update
sudo apt install python3-pip
```

`pip freeze` <--- Nos detalle todas las librerias (de Python) que tenemos instaladas.


## PATH

En nuestra terminal, ejecutamos:
`echo $PATH`
`cat .profile`     <<== Lugar donde existe el archivo zshrc
		              Este archivo se ejecuta CADA VEZ, que abrimos una nueva terminal.

Nos copiamos las dos referencia a los PATH:

```
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/.local/bin" ] ; then
    PATH="$HOME/.local/bin:$PATH"
fi
```

### Breve explicacion:

Si existe el directorio $HOME/bin, lo agrega al PATH.
Si existe el directorio $HOME/.local/bin, lo agrega al PATH.

Esto resuelve todos los problemas de `Warning` en referencia a los PATH.

### Siguiente paso: 
code .zshrc      <=== Abrimos ese archivo con nuestro editor de codigo fav (Visual Studio Code)

## ENVIROMENTS
Variables de entorno.

Instalacones necesarias:

### Pyenv

Prerequisitos: 
```
sudo apt-get update; sudo apt-get install make build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm \
libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
```

Instalacion:
` git clone https://github.com/pyenv/pyenv.git ~/.pyenv`

Recordar que, si ejecutamos en nuestra terminal:
`pwd` nos mostrara el directorio en el que nos encontramos.

La indicacion ~/.pyenv inda que, la instalacion se realizara en nuestro directorio home.

Si ahora en nuestra terminal, ejecutamos:
`ls -la` Flag -ls para listar, -la para que nos muestre los archivos ocultos, nos encontraremos que efectivamente, se ha instalado pyenv:


```
drwxr-xr-x 12 brahi brahi  4096 Nov 21 12:11 .pyenv
```

### Pyenv virtualenv

En primera instancia, necesitamos agregar nuestras variables de entorno a nuestro archivo .zshrc

```
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init --path)"' >> ~/.zshrc
```

### Nota importante: 

En esta instancia, efectivamente tenemos Pyenv, PERO, tendremos acceso a el unicamente, al abrir una nueva terminal. Porque, recordar que el archivo .zshrc se ejecuta CADA VEZ, que se abre una nueva instancia de la misma.

Ahora podemos ejecutar (en una nueva terminal): `pyenv`


## Lecturas sugeridas:

[Otorgar permisos en Kali](https://www.hostinger.es/tutoriales/cambiar-permisos-y-propietarios-linux-linea-de-comandos/)

[Rutas relativas vs Rutas absolutas](https://www.zeppelinux.es/rutas-relativas-y-rutas-absolutas-en-linux/)
