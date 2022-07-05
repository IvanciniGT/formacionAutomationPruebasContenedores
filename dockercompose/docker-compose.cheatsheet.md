docker-compose    -f FICHERO        COMANDO
                 # si el fichero docker-compose.yaml no se llama así, cosa que no haremos nunca
                 # Esto también es util si quiero ejecutar el comando desde una carpeta que no contiene el fichero
                 
                                    COMANDOS:
                                    up          Crea y arranca los contenedores
                                                Y además, bloquea la terminal mostrando los logs de los contenedores
                                        -d      MODO DETACHED: Sin bloquear la consola ni mostrar los logs
                                    down        Para y borra los contenedores
                                    start       Arranca los contenedores que ya hayan sido creados de antemano
                                    stop        Para los contenedores sin borrarlos
                                    restart     ...