FROM php:7.0.27-apache
MAINTAINER angelroybernal


# Install needed software and dependencies
RUN DEBIAN_FRONTEND=noninteractive \
apt-get update \
&& apt-get install -qy \
git \
libicu-dev \
libmcrypt-dev \
libpng-dev \
libxml2-dev \
nano \
mysql-client \
dnsutils \
&& apt-get clean


# Install PHP extensions
RUN docker-php-ext-install \
gd \
intl \
mbstring \
mcrypt \
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
