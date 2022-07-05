docker [TIPO_OBJETO] [VERBO] <args>

TIPO_OBJETO:
- container     list    create  rm      start   stop    restart inspect logs    exec
- image         list    rm      pull    push    inspect
- volume        list
- network       list
- secret        list

# CONTAINERS:

docker container list               Nos muestra los conetendores en ejecución   =    docker ps
                        --all       Muestra los parados y los en ejecución

docker container create 
    --name NOMBRE
    -p     [IP_HOST:]PUERTO_HOST:PUERTO_CONTENEDOR
    -v     ruta_host:ruta_contenedor
    -e     VARIABLE_ENTORNO=VALOR
    [registry/]repo:tag

docker [container]  start       NOMBRE_DEL_CONTENEDOR 
                    stop
                    restart
                    rm                                      ( -f : borrar el contenedor aun estando arrancado)
                    inspect
                    logs
                    attach

docker exec     NOMBRE_CONTENEDOR [COMANDO]
            -it -> Se abra una terminal interactiva para ir lanzando nuevos comandos:
                bash
                sh
                mysql
                python
                
docker run  --name NOMBRE
    -p     [IP_HOST:]PUERTO_HOST:PUERTO_CONTENEDOR
    -v     ruta_host:ruta_contenedor
    -e     VARIABLE_ENTORNO=VALOR
    -d                                                  Ejecuta en modo dettached
    [registry/]repo:tag
    
    Este comando hace:
        docker container create
        + docker start
        + docker attach
    Tiene sentido usarlo para :
    - Pruebas de concepto
    - Ejecutar contenedores que dentro lo quengan sea un script o un comando.