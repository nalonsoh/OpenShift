# spring-boot-app
FROM openjdk:8-alpine

MAINTAINER Noel Alonso Hernández <nalonsoh@viewnext.com>

# TODO: Rename the builder environment variable to inform users about application you provide them
# ENV BUILDER_VERSION 1.0

# Set labels used in OpenShift to describe the builder image
LABEL io.k8s.description="Platform for building spring-boot-app" \
      io.k8s.display-name="builder spring-boot-app" \
      io.openshift.expose-services="8080:http" \
      io.openshift.tags="builder, spring-boot-app"\
# Defines the location of the S2I
      io.openshift.s2i.scripts-url=image:///usr/local/s2i

# Install the required software (Maven)
RUN wget  -P /home http://apache.rediris.es/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.tar.gz \
	&& tar -xvzf /home/apache-maven-3.*-bin.tar.gz -C /home \
	&& rm /home/apache-maven-3.*-bin.tar.gz\
	&& adduser -D -u 1001 1001

ENV PATH="/home/apache-maven-3.6.0/bin:${PATH}"

# Copy the S2I scripts from ./s2i/bin/ to /usr/local/s2i when making the builder image
COPY ./s2i/bin/ /usr/local/s2i

# Set the default port for applications built using this image
EXPOSE 8080

USER 1001

# TODO: Set the default CMD for the image
CMD ["/usr/local/s2i/usage"]
