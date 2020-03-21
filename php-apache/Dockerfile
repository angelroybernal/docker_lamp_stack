FROM php:7.4-apache
MAINTAINER angelroybernal


# Install needed software and dependencies
RUN DEBIAN_FRONTEND=noninteractive \
apt-get update \
&& apt-get install -qy \
    git \
    libzip-dev \
    libicu-dev \
    libmcrypt-dev \
    libonig-dev \
    libpng-dev \
    libxml2-dev \
    default-mysql-client \
    dnsutils \
&& apt-get clean


# Install PHP extensions
RUN pecl install mcrypt-1.0.3 && \
docker-php-ext-install \
    gd \
    intl \
    mbstring \
    opcache \
    pdo_mysql \
    soap \
    zip


RUN a2enmod headers \
&& a2enmod rewrite
COPY 000-default.conf /etc/apache2/sites-available/000-default.conf

# Install and setup composer
RUN curl -sS https://getcomposer.org/installer | php \
&&  mv composer.phar /usr/local/bin/composer


EXPOSE 80
CMD ["apache2-foreground"]
