FROM phpdockerio/php:8.2-fpm

WORKDIR "/application"

# Fix debconf warnings upon build
ARG DEBIAN_FRONTEND=noninteractive

# Install selected extensions and other stuff
RUN apt-get update --fix-missing
RUN apt-get autoremove
RUN apt-get dist-upgrade -y
RUN apt update -y
RUN apt-get -y install software-properties-common
RUN apt-get -y --no-install-recommends install php8.2-mysql \
    php8.2-bcmath \
    php8.2-intl \
    php-mongodb \
    php8.2-soap \
    php8.2-xmlrpc \
    php8.2-xsl \
    php8.2-pgsql \
    php-yaml \
    php8.2-gd \
    libfontconfig1 \
    libxrender1 \
    libxext6 \
    rsync \
    acl \
    vim \
    jq \
    php8.2-xdebug \
    php8.2-redis \
    npm \
    make
RUN add-apt-repository ppa:ondrej/php
RUN apt-get update
RUN apt-get -y install php8.2-amqp

# Install git
RUN apt-get update
RUN apt-get -y install git
RUN apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

RUN rm /etc/localtime && ln -snf /usr/share/zoneinfo/Europe/Warsaw /etc/localtime && echo Europe/Warsaw > /etc/timezone

# Change version from 8 to 7.4
RUN rm /etc/alternatives/php && ln -s /usr/bin/php8.2 /etc/alternatives/php

# Install swagger-cli for swagger doc builds
RUN npm install -g @apidevtools/swagger-cli
