# docker te permite construir distribuir y ejecutar cualquier aplicacion en cualquier lado.
# Problemas al construir software
- Entorno de desarollo 
- Dependencias(paquetes)
- Entorno de ejecucion
- Equivalencia con entrono productivo(sincronismo en el equipo de desarollo)
- Servicios externos(api,data base).
# Distribuir software
El sofware debe ser transformado en un artefacto o varios que puedan ser ejecutados donde sea requerido: web , aplicaciones moviles.
- Divergencia de repositorios
- Versiones de artefactos
- versionado
# Ejecutar software 
Implementacion de la solucion en el ambiete de produccion (subir a produccion) 
problemas:
- Compativilidad con el entorno productivo.
- dependencias
- disponibilidad de servicios externos.
- Recursos de hardware.
# VIRTUALIZACION
Docker en vez de usar maquinas virtuales usa contenedores
El fin de los contenedores es  brindan una forma estandarizada y reproducible de empaquetar aplicaciones y sus dependencias, garantizando su portabilidad, aislamiento y eficiencia, y permitiendo una implementación y escalabilidad rápidas.
# ARQUITECTURA
![image](https://github.com/molinajr11/docker/assets/105083946/dc34cbbd-0664-4a4c-9430-ef10a52b5c53)
# Que es un contenedor:
- Lugar donde se ejecutan las aplicaciones.
- Es una agrupacion de procesos que corren en nativamente una maquina pero esta aislado del sistema.
- Es una unidad logica,  Los procesos que se ejecutan adentro de los contenedores ven su universo como el contenedor lo define, no pueden ver mas allá del contenedor, a pesar de estar corriendo en una maquina más grande.
# Ciclo de vida de un contenedor:
Todos los contenedores cuando se ejecuntan tiene un proceso main y este va a tener la id 1: si este porceso se detiene por que asi se programo o se mata manualmente el contenedor se apagara 
# Bind Mounts
- Es compartir archivos, directorios datos entre contenedores y nuestra maquina.
- une una ruta de la maquina que ejecuta el contenedor con una ruta dentro del contenedor
- permite sacar y meter datos de un contenedor
- riesgo acceso al contenedor a un parte de nuestro disco
# Volumenes 
- Es un espacio en memoria administrado solo por docker.
- guarda infromacion
- solo docker puede acceder a la informacion desde un contenedor
- si el contenedor se elimina el volumen persiste.
- se puede compartir esta informacion entre contenedores
# Dockerfile
- Es la base para construir contenedores apartir de imagenes.
- Con un dockerfile se pueden construir infinitos contenedores
- Las imagenes son una forma logica de hablar de un conjunto de capaz 🔦
- Creacion de un dockerfile:
🏠 FROM: ubuntu:latest  imagen base
-> cada instruccion genera una capa
  RUN: build time     
# Docker-Compose 
- Es un archivo que se usa para administrar multiples servicios de contenedores.
- facilita el despliege de aplicaciones con multiples contenedores.
# Ejemplo y contenido de un archivo compose
version: '3'  # Versión de Docker Compose

services:
  # Servicio de la base de datos MySQL
  db:
    image: mysql:5.7
    container_name: mysql_db
    environment:
      MYSQL_ROOT_PASSWORD: password
      MYSQL_DATABASE: mi_basededatos
    volumes:
      - mysql_data:/var/lib/mysql

  # Servicio de la aplicación Spring Boot
  app:
    image: nombre_de_tu_imagen_de_spring_boot
    container_name: mi_aplicacion
    ports:
      - "8080:8080"
    depends_on:
      - db  # Asegura que el servicio de la base de datos esté disponible antes de iniciar la aplicación
    environment:
      SPRING_DATASOURCE_URL: jdbc:mysql://db:3306/mi_basededatos
      SPRING_DATASOURCE_USERNAME: root
      SPRING_DATASOURCE_PASSWORD: password

volumes:
  mysql_data:  # Volumen para almacenar los datos de la base de datos

  ![image](https://github.com/molinajr11/docker/assets/105083946/d72f845d-cf3f-4d7a-a254-59abeaf9656e)

