# Guía 5 FWA - Aplicación Rick and Morty con Vue

Este repositorio contiene un proyecto que consume la API de Rick and Morty, creado con Vue como parte de la Guía 5 de FWA. La aplicación permite ver todos los personajes de la serie y filtrarlos, demostrando cómo crear una aplicación web interactiva que consume APIs externas y cómo desplegarla utilizando Docker.

## Características

- Visualización de personajes de Rick and Morty
- Filtrado de personajes
- Consumo de la API de Rick and Morty
- Interfaz de usuario intuitiva creada con Vue

## Prerrequisitos

- [Git](https://git-scm.com/) (opcional, para clonar el repositorio)
- [Node.js](https://nodejs.org/)
- [npm](https://www.npmjs.com/) (viene incluido con Node.js)
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)

## Instrucciones de uso

### Paso 1: Obtener el código

Tienes dos opciones para obtener el código del proyecto:

#### Opción A: Clonar el repositorio (requiere Git)

1. Abre una terminal.
2. Ejecuta el siguiente comando:
   ```
   git clone [URL_DEL_REPOSITORIO]
   ```
   Reemplaza `[URL_DEL_REPOSITORIO]` con la URL real del repositorio.

#### Opción B: Descargar como ZIP

1. Ve a la página principal del repositorio en GitHub.
2. Haz clic en el botón "Code" y selecciona "Download ZIP".
3. Descarga el archivo ZIP y descomprímelo en tu computadora.

### Paso 2: Instalar dependencias

1. Abre una terminal en el directorio del proyecto.
2. Ejecuta el siguiente comando para instalar las dependencias:
   ```
   npm install
   ```

### Paso 3: Ejecutar la aplicación localmente (opcional)

Si deseas probar la aplicación antes de crear la imagen Docker, puedes ejecutarla localmente:

```
npm run serve
```

Abre tu navegador y visita la URL que se muestra en la terminal (usualmente `http://localhost:8080`).

### Opción 1: Construir y ejecutar la imagen Docker localmente

1. Asegúrate de estar en el directorio del proyecto.
2. Construye la imagen Docker:
   ```
   docker build -t [nombre-imagen] .
   ```
3. Ejecuta el contenedor:
   ```
   docker run -d -p 8080:80 [nombre-imagen]
   ```
4. Abre tu navegador y visita `http://localhost:8080` para ver la aplicación.

### Opción 2: Utilizar la imagen preconfigurada de Docker Hub

1. Abre Docker Desktop.
2. Inicia sesión en tu cuenta de Docker (si aún no lo has hecho).
3. Abre una terminal y ejecuta:
   ```
   docker pull byluisr/rick-morty-site
   ```
4. En Docker Desktop, busca la imagen descargada.
5. Haz clic en el botón "Run" junto al nombre de la imagen.
6. Configura el nombre del contenedor y el puerto (por ejemplo, 8080).
7. Asegúrate de que el puerto 8080 no esté siendo utilizado por otra aplicación.
8. Ejecuta el contenedor.
9. Abre tu navegador y visita `http://localhost:8080` para ver la aplicación.

## Notas adicionales

- Si tienes problemas para abrir Docker Desktop, búscalo en la barra de búsqueda de Windows o en el icono de la ballena en la barra de tareas (junto al reloj).
- Asegúrate de que Docker Desktop esté en ejecución antes de intentar construir o ejecutar contenedores.
