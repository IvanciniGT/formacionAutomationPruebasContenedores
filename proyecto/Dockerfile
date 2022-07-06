# REPO DE GIT
# Descargar el codigo.                                  git
# Compilar/empaquetar                                   maven + java
# Instalar la app resultante (WAR) en un tomcat         tomcat


FROM maven:3.8-openjdk-8 AS empaquetador
COPY . /miweb/
WORKDIR /miweb
RUN mvn package

FROM bitnami/tomcat:9.0.64

COPY --from=empaquetador /miweb/target/webapp.war /app/
ENV ALLOW_EMPTY_PASSWORD=yes

LABEL maintainers="Ivan Osuna Ayuste <iam@ivan.com>"
LABEL license="MIT"
LABEL home="http://miwebapp.com"
