FROM ubuntu

# Rust installation
RUN curl --proto '=https' --tlsv1.3 https://sh.rustup.rs -sSf | sh -s -- -y

RUN apt-get update

# PHP 
RUN apt-get install software-properties-common ca-certificates lsb-release apt-transport-https  -y
RUN add-apt-repository ppa:ondrej/php

RUN apt-get install -y \
    curl \
    git \
    golang \
    sudo \
    vim \
    wget \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# PHP Installation
RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -yq php8.2 \
    php8.2-bcmath \
    php8.2-fpm\
    php8.2-xml\
    php8.2-mysql \
    php8.2-zip\
    php8.2-intl\
    php8.2-ldap\
    php8.2-gd \ 
    php8.2-cli\
    php8.2-bz2\
    php8.2-curl\
    php8.2-mbstring\
    php8.2-pgsql \
    php8.2-opcache \
    php8.2-cgi

ARG USER=coder
RUN useradd --groups sudo --no-create-home --shell /bin/bash ${USER} \
    && echo "${USER} ALL=(ALL) NOPASSWD:ALL" >/etc/sudoers.d/${USER} \
    && chmod 0440 /etc/sudoers.d/${USER}
USER ${USER}

ENV PATH="/root/.cargo/bin:${PATH}"

WORKDIR /home/${USER}