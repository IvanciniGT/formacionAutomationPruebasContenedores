Jenkins: http://172.31.12.156:8080
Sonar:   http://172.31.12.156:8081


Jenkins va a pedir a sonar que haga un analisis del codigo
    URL sonar + credencial
    
Sonar cuando acabe, avisa a Jenkins de que el analisis ha concluido, para que pueda mirar los resultados
    URL Jenkins

En el host donde se ejecuta el pipeline:
    carpeta local < codigo git
    CONTENEDOR1: COMPILAR: crea un contenedor con la imagen que yo quiera y le inyecta al contenedor el
        codigo descargado mediante un volumen
    CONTENEDOR2: TEST
    CONTEENDOR3: EMPAQUETADO
    clean
    
    
    
/job/Prueba/lastSuccessfulBuild/artifact/proyecto/target/webapp.war
^^^^^^^



Devops:
    Integración continua ****
        Tener continuamente en el entorno de Integración (Preproduccion, test, pruebas)
        la ultima versión del codigo de los desarrolladores, obtenida desde un repo de SCM
        y sometida a pruebas autoamtizadas de distinta naturaleza
            Unitarias
            Calidad de codigo
    Entrega continua.   ****
        Que mi cliente siempre pueda acceder a la ultima version de mi artefacto, automaticamente
            Normalemnente no lo dejo en el jenkins, lo llevo a:
                nexus
                artifactory
                docker hub
    Despliegue continuo
        Si ese artecafto lo instalo automaticamente en el entorno de producción de mi cliente(s)


Granja de seleniums: Selenium Grid
    chrome + driver
    firefox + driver
    edge + driver

app
prueba
