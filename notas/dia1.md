# Contenedor

Entorno aislado dentro de un SO Linux donde ejecutar procesos.
Entorno aislado... en cuanto a qué?
- Un contenedor tiene su propia configuración de red -> IP
- Un contenedor tiene su propio Filesystem, independiente al del host
- Un contenedor tiene sus propias variables de entorno, independientes a las del host
- Un contenedor puede tener limitación de acceso a recursos del hierro (CPU, memoria,...)

La contenedorización es una tecnología que permite empaquetar, distribuir, instalar y ejecutar aplicaciones
sin los problemas que teníamos con unos modelos más tradicionales.

Los contenedores ofrecen una forma estandarizada de operar/instalar apps:
- Instalar
- Arrancar
- Configurar
- Parar
- Desinstalar
- Reiniciar
- Logs

Los contenedores los creeamos desde una IMAGEN DE CONTENEDOR.

# Qué es una imagen de contenedor

Un triste fichero comprimido (tar) que contiene una estructura de carpetas propia de un SO Posix (linux, unix)
con una serie de programas ya instalados de antemano y configurados por alguien.
Adicionalmente una imagen de contenedor lleva una configuración de ese entorno aislado (CONTENEDOR)
que se generará desde está imagen de contenedor.

Las imágenes de contenedor se alojan en registries de repos de imágenes de contenedores:
    docker hub
    quay.io     redhat
    nexus | artifactory
    gitlab artifacts


- Como un contenedor con ya cosas preinstaladas
- Base de una configuración de la que partir para montar otra

---

Qué es Unix®?  2 especificaciones de cómo montar un SO (POSIX, SUS)
Qué era Unix®? Era un SO... hasta los 2000 y poco que lo dejaron de hacer. 
             AT&T labs Bell
Oracle: Solaris -> SO Unix®
HP:     HP-UX
IBM:    AIX
Apple:  MacOS

BSD386 -> Cagada grande -> BSD (freeBSD, netBSD, MacOS) 
GNU    -> Cagada igual de grande -> kernel
            GNU is Not Unix
Linus torvalds -> Linus' UNIX -> GNU + Linux
                                 75%    25%
Android -> linux + Google libraries

     App1  +  App2  +  App3         Problemas:
    ------------------------            Las apps que tenemos instaladas pueden requerir 
        SO                                  dependencias / config. incompatibles
    ------------------------            Imaginad que app1 (bug) -> 100% CPU, Memoria, Disco duro
        HIERRO                              App1 OFF.... App(n) OFF
                                        App2 potencialmente podría acceder a los datos de app1
                                        
                                        
    ------------------------        Problemas:
     App1   |  App2 + App3              Desperdicio de recursos que te cagas!!!
    ------------------------            Merma del rencimiento
     SO 1   |   SO 2                    Complejidad de la configuración
    ------------------------            Snapshots
     MV 1   |   MV 2
    ------------------------
        Hipervisor:
    VMWare, HyperV, KVM, citrix
    Virtualbox
    ------------------------
        SO
    ------------------------
        HIERRO



    ------------------------        
     App1   |  App2 + App3          
    ------------------------        
     C 1    |  C 2
    ------------------------
    Gestor de contenedores:
    Docker, podman, crio, 
    containerd
    ------------------------
        SO Linux (UNICO SO)
    ------------------------
        HIERRO
    

Kubernetes = Gestor de gestores de contenedores
    Kubernetes (k8s, k3s, tamzu, openshift)
Granja de máquinas: Cluster > REDUNDANCIA (HA+Escalabilidad)
    
    Kubernetes:
        Maquina 1
            Gestor de contenedores: crio | containerd
        Maquina 2
            Gestor de contenedores: crio | containerd
        Maquina N
            Gestor de contenedores: crio | containerd




FileSystem, de un sistema POSIX:
/
    root/           Carpeta del usuario root
    mnt/            Punto de montaje
    bin/            Comandos binarios
    var/            Datos de los programas / aplicaciones
    opt/            Programas / aplicaciones
    tmp/            temporales
    home/           carpetas de usuario
    etc/            configuraciones


Instalar en mi IvanPC -> mariaDB
0- Tengo un ordena con Windows instalado
1- Descargar un instalador de mariadb
2- Ejecutar el instalador -> Instalación de MariaDB
3- Configurar el MariaDB a mi gusto

c:\archivos de programa\mariadb\.... -> ZIP -> email -> descomprimís en el mismo sitio.

# Docker Inc

- docker engine <<<< A esto habitualmente nos referimos cuando decimos DOCKER
- docker-compose         Tan solo es otro cliente del demonio de docker
- docker desktop for windows / mac
- docker - swarm
- docker hub

- portainer: Otro cliente del demoino de docker

# Docker engine

Es un gestor de contenedores, que tiene una arquitectura cliente / servidor
- Hay un servicio que que en ejecución en segundo plano (el demonio de docker): dockerd
                                                                                  ^^
- Tenemos una herramienta cliente que nos permite interacturar con ese demonio: docker

# Instalar docker: 
Debian | Ubuntu:    apt install docker
Redhat | centos:    yum install docker
Fedora:             dnf install docker

docker | docker-compose             HOY

docker-compose | dockerfile         MAÑANA

Miercoles:  Levantar algunos entornos de pruebas 

# DEV-->OPS

Cultura / filosofia de la AUTOMATIZACION de qué? de todo lo que hay entre el desarrollo y la operación 
de un sistema informático

Planificación. Dificilmente automatizable
Desarrollo.    Dificilmente automatizable   -> SourceCodeManager -> Sistema de Control de Versiones 
Empaquetado / Build                                                 git
    JAVA        maven gradle sbt                                        github
    JS          npm, yarn webpack                                       gitlab
    Microsft    msbuild, nuget                                          bitbucket
    python      poetry
-----------------------------------------------------> Desarrollo ágil <> Metodologñia agil de desarrollo de software
Pruebas.        Diseño de la prueba. Malamente
                Ejecución de la prueba
                
    Pruebas estáticas . Pruebas donde no es requerido ejecutar el código
        Calidad del código.     Sonarqube, findbugs, lint
    Pruebas dinámicas . Pruebas donde es requeerido poner el codigo en marcha
        Pruebas funcionales
            Unitarias       Probar un modulo unitario/independiente de código
                                Junit, TestNG
                                MsTest
                                unittest
                                    postman
                                    soapui
            Integración     Probar las comunicaciones
                                Junit
            Sistema         Probar que funciona como debe funcionar / requisitos
                    Web - Frontend      Selenium
                    Web - Backend       Postman, SoapUI, Karate
                    App                 Appium
            Aceptación      Proabr lo que el cliente espera del sistema
        Pruebas no funcionales
            Rendimiento         loadrunner Jmeter
            Carga
            Estres
            HA
            UX
        Las pruebas las hacemos en un entorno independiente, especifico para pruebas:
            Entorno de pre-producción
                    de certificación
                    de pruebas
                    de integración
---------------------------------------------------------> Integración continua - CI
                        Tener continuamente la última versión del código de los desarrollares en 
                        un entorno de integración estando sometido a pruebas automatizadas

Generación de un artefacto y puesta en mano del cliente de ese artefacto
---------------------------------------------------------> Entrega continua     - Continuous Delivery
Instalar el artefacto en el entorno de producción en automatico
---------------------------------------------------------> Depsliegue continua  - Continuous Deployment
    Kubernetes 
        Contenedores

Nos falta una herramienta que orqueste todos estos trabajos
Que llame al git
          al maven
          al selenium
          al jmeter
          al sonarqube

Servidor de automatización, servidor de CI/CD:
- Jenkins               | Crean los entornos de pruebas dentro de contenedores donde ejecutar las pruebas
- TravisCI
- Bamboo
- AzureDevops
- Gitlab CI/CD
- Github Actions

Por qué usamos hoy en día contendores en los entornos de Integración (test) ? 
- Entornos de usar y tirar! Siempre partimos del mismo escenario
- No necesito teenr unas maquinas paradas mucho tiempo
- Entornos aislados
- Facilmente instalables / operables
- Al final es lo que va a producción

Back  -> Java Springboot
    Front -> JS - ReactJS
    App Android -> kotlin
    
En un entorno de pruebas necesito: MONTONONES DE CONTENEDORES:
- Backend - JAVA
    - gradle | maven < Contenedor de compilación y empaquetado
        ----> empaquetado
        - Pruebas unitarias
- Despliegue de la app BACKEND (servicios web REST/SOAP)
    - Java mas tradicional (Spring) -> Servidor de apps Java: Tomcat
                                                               weblogic
                                                               jboss
                                                               websphere
                                                               liberty
    - Java mas modernito (Springboot) -> Servidor de apps Java integrado: Tomcat
    - Necesito un entorno con la maquina virtual de JAVA: Contenedor de despliegue de la app de back
    - postman -> Contenedor de pruebas de postman
    - jmeter ->  Contenedor para pruebas de rendimiento
    - BBDD (mariaDB) -> contenedor de BBDD
    - Redis (cache)  -> contenedor 
    - Kafka, activeMQ, rabibit (sistemas de mensajería) -> Contendor

- frontend:
    - App web:
        - Servidor web (nginx, apache)-> JS -> Contenedor de despliegue
        - Selenium (donde lanzar las pruebas) -> Java, Python, C# -> contenedor
        - Navegador -> Contenedor - Firefox + Chrome
    - App para moviles: 
        Appium: contenedor
        Emulador de un telefono movil: Appium -> contenedor


Herramienats para crear contenedores:
- docker: Contenedor a contenedor
- docker-compose: más cómodo: Apliaciones multicontenedor
    -> Ficheros YAML: damos la especificación de un montonon de conteendores que queremos crear
            -> git
    $ docker-compose -f FICHERO up
                                down

# Cuando creamos un conteendor: 

## Que info debemos suministrar:

- Imagen de partida
- Nombre de contenedor
- Trabajará en un puerto... cómo lo hago accesible: NAT / Mapeo de puertos a nivel del host
    - Redirecciones de puertos
- Establer configuraciones en el programa que se ejecute dentro:
    - Variables de entorno
- Volumenes:
    - Es una carpeta compartida entre el host y el contenedor
            HOST                    CONTENEDOR
            /var/datos/app1     ->  /datos
    Pa que vale esto?
    - Dar persistencia a la información... 
        - Si yo paro un contenedor y lo vuelvo a arrancar... sigue ahi el dato ? SI 
        - Si se elimina un contenedor y lo vuelvo a crear.... ahi ya no *** Para CI: Esto es poco relevante.... o poquito relavante algo si
                -   Informe
    - Compartir archivos y carpetas entre contenedores                  *** Esto es muy util en CI
                    Contenedor de empaquetado (MAVEN) *.jar *.war -> Contenedor de despliegue (JAVA)
- Limitacion de acceso a recursos de harware
    - como mucho que use 1 CPU
    - como mucho 2 Gbs de ram


Servidor web: nginx : puerto por defecto es el 80
curl http://IP:80
Red virtual de docker: 172.17.0.0/16
                       172.17.0.2 Primer contenedor
                       