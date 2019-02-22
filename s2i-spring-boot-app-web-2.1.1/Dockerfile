# spring-boot-app
FROM noelalonso1/spring-boot-app-builder:latest

MAINTAINER Noel Alonso Hernández <nalonsoh@viewnext.com>

# Copiar el pom.xml
COPY ./dummy-app /home/1001/dummy-app

USER root
RUN chown -R 1001:1001 /home/1001/dummy-app
USER 1001

# Descargar dependencias del POM 
# (hacemos un install en lugar de un dependency:resolve para que se descargue tambien los plugins)
RUN mvn clean install -f /home/1001/dummy-app