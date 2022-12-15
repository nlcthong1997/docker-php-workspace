FROM ubuntu:latest

# Resolve avoid question during the Docker build?
ARG DEBIAN_FRONTEND=noninteractive

# Install tools
RUN apt-get update && apt-get install -y \
    zip \
    unzip \
    git \
    curl \
    vim \
    nano \
    apache2

# Add ppa:ondrej/php PPA repository which has the latest build packages of PHP. 
RUN apt-get update && apt-get install -y software-properties-common
RUN add-apt-repository ppa:ondrej/php

# Install PHP 7.4
RUN apt-get update && apt -y install php7.4

# Enable and install php74, php extentions
#RUN apt install -y php7.4-{cli, json, common, mysql, zip, gd, mbstring, curl, xml, bcmath, fpm, dom}
RUN apt-get install -y \
    php7.4-cli \
    php7.4-json \
    php7.4-common \
    php7.4-mysql \
    php7.4-zip \
    php7.4-gd \
    php7.4-mbstring \
    php7.4-curl \
    php7.4-xml \
    php7.4-fpm \
    php7.4-dom \
    php7.4-bcmath

# Install composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
    php composer-setup.php --install-dir=/usr/local/bin --filename=composer && \
    rm -rf composer-setup.php

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Set working directory
WORKDIR /var/www/html

EXPOSE 80

#ENTRYPOINT ["/usr/sbin/apache2", "-k", "start"]
ENTRYPOINT [ "apachectl" ]
CMD [ "-D", "FOREGROUND" ]
