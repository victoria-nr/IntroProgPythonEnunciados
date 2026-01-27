# Entorno Python con PyPAS en Docker

Este proyecto permite a los alumnos trabajar con **Python** y **PyPAS** dentro de un contenedor,
sin necesidad de permisos de administrador en el ordenador.

## 🚀 Pasos a seguir

```bash
# 1. Crear el directorio de trabajo para los ejercicios y dar permisos escritura
mkdir app
chmod 777 app

# 2. Genera el fichero `.env` con tu usuario ejecutando estos comandos:
echo "UID=$(id -u)" > .env
echo "GID=$(id -g)" >> .env

# 3. Abrir la carpeta app en Visual Studio Code

# 4. En el terminal, dentro de la carpeta python-pypas-docker, levantar el contenedor con Docker Compose
docker compose up -d

# 5. Entrar en el contenedor
docker exec -it python_pypas bash

# 6. Comprobar que PyPAS funciona
pypas list

# 7. Empezar a trabajar (ejemplo)
pypas get add


