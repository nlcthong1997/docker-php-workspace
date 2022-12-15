FROM amazonlinux:latest

# Install tools
RUN yum update -y && yum -y install \
    amazon-linux-extras \
    zip \
    unzip \
    wget \
    curl \
    net-tools \
    mysql \
    git

# Enable and install php74, php extentions
RUN yum clean metadata
RUN amazon-linux-extras enable php7.4
RUN yum -y install php \
    php-pear \
    php-cgi \
    php-common \
    php-curl \
    php-mbstring \
    php-gd \
    php-mysqlnd \
    php-gettext \
    php-bcmath \
    php-json \
    php-xml \
    php-fpm \
    php-intl \
    php-zip \
    php-imap \
    php-dom

# Install composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
    php composer-setup.php --install-dir=/usr/local/bin --filename=composer && \
    rm -rf composer-setup.php

# Clear cache
RUN yum clean all

# Set working directory
WORKDIR /var/www/html

# Create user www-data
RUN useradd www-data

# Add user www-data and root to group www-data
RUN usermod -a -G www-data www-data
RUN usermod -a -G root www-data
