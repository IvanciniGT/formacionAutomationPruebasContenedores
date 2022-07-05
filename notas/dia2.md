# Contenedor

Entorno aislado en un SO Linux donde ejecutamos procesos.
Aislado:
- Su propia configuración de red -> IP
- Su propio filesystem
- Sus propias variables de entorno 
- Podría tener una limitación de acceso a recursos del hierro del host

Los contenedores se crean desde: Imagenes de contenedor

# Imagen de contenedor:

Un fichero comprimido que contiene una estructura de carpetas compatible con POSIX
Y además una serie de programas ya instalados y configurados por alguien.

Las imagenes se guardan en registries de repos de imagenes, como docker hub

Al crear un contenedor, que información debemos suministrar:
- Nombre
- Imagen            [registry/] repo:tag
                    artefactos.iochannel.tech/    ivancinigt/iochannel-ssh-container          latest
- Puertos para hacer redirecciones a nivel del host. Motivación:
    - Poder acceder al servicio que ofrezca el conteendor desde una red distinta a la de docker
    - El disponer de una dirección fija que no cambie para ccceder al servicio
- Volumenes: Carpeta compartida entre host y contenedor (los datos realmente se guardan en el host)
    Persistencia de datos.... transborrado del contenedor
    Compartir datos entre contenedores
    Inyectar ficheros o carpetas al filesystem del contenedor desde el host
- Variables de entorno: Configurar compartientos de los procesos de dentro del contenedor
- Limitaciones de recursos hardware

El host tiene IPs:
- docker: 172.17.0.1
- loopback: 127.0.0.1 (localhost)
- eth: 172.31.12.156
 

Lenguajes informáticos:
    Programación
    Consula a bases de datos
    Lenguajes de marcado
    Lenguajes de modelado

YAML es un lenguaje de marcado de información de proposito general, como XML, JSON, HTML(de propósito específico)

YAML - YAML ain't markup language. Inspirado en python. Pensado para seres humanos, a diferencia de XML o JSON
 XML \
HTML  >  etiquetas TAGs         <p>Parrafo <b>negrita></b> </p>
SGML /
  ML: Markup language