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
  
