FROM ubuntu:22.04

LABEL maintainer="Ganesh Raj Joshi<jjoshiganeshraj@gmail.com>"

ARG WWWGROUP
ARG NODE_VERSION=18
ARG POSTGRES_VERSION=14

WORKDIR /var/www/nydoz-react

ENV DEBIAN_FRONTEND noninteractive
ENV TZ=UTC

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN apt-get update \
    && apt-get install -y gnupg gosu curl ca-certificates zip unzip git libcap2-bin libpng-dev dnsutils

RUN apt-get install -y software-properties-common \
    && apt-get install -y nginx \
    && apt-get install -y systemctl \
    && apt-get install -y nano

CMD npm install -g @angular/cli

RUN groupadd --force -g $WWWGROUP laravel-1-developers
RUN useradd -ms /bin/bash --no-user-group -g $WWWGROUP -u 1337 angular-developer

COPY start-container /usr/local/bin/start-container
RUN chmod +x /usr/local/bin/start-container

EXPOSE 4200

ENTRYPOINT ["start-container"]
