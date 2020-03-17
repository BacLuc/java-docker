FROM ubuntu:18.04 as base

ARG DEBIAN_FRONTEND=noninteractive

ARG JAVA_VERSION
ARG MAVEN_VERSION

RUN apt-get update && apt-get install -y \
        apt-transport-https \
        libgtk2.0-0 libwebkit2gtk-4.0-37 libasound2 \
        git ant fonts-liberation \
        openjdk-${JAVA_VERSION}-jdk \
        maven

RUN useradd -ms /bin/bash app

RUN mkdir /home/app/app
RUN mkdir /home/app/.m2
RUN chown -R app:app /home/app

VOLUME /home/app/.m2

WORKDIR /home/app/app

USER app

############

FROM base as vnc

RUN apt-get update && apt-get install -y \
        apt-transport-https \
        libgtk2.0-0 libwebkit2gtk-4.0-37 libasound2 \
        git ant xvfb x11vnc fonts-liberation \
        openjdk-${JAVA_VERSION}-jdk \
        maven

COPY start-display /start-display
RUN chmod +x /start-display


ENTRYPOINT ["/start-display"]