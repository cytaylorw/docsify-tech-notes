# Dockerfile Examples

## Apache Base Image

Update the Dockerfile based on the actual requirement:

- Update the PHP version of the base image
- Add/Remove the system dependencies and PHP modules.

```docker
#start with our base image (the foundation) - version 7.4.15
FROM php:7.4.15-apache

#install the system dependencies and enable PHP modules
RUN apt-get update && apt-get install -y \
      libicu-dev \
      libpq-dev \
      libmcrypt-dev \
      git \
      zip \
      unzip \
      libzip-dev \
    && pecl install mcrypt-1.0.4 \
    && docker-php-ext-enable mcrypt \
    && rm -r /var/lib/apt/lists/* \
    && docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd \
    && docker-php-ext-install \
      intl \
      pcntl \
      pdo_mysql \
      pdo_pgsql \
      pgsql \
      zip \
      opcache \
      sockets

#install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin/ --filename=composer

#set our application folder as an environment variable
ENV APP_HOME /var/www/html

#change uid and gid of apache to docker user uid/gid
# RUN usermod -u 1000 www-data && groupmod -g 1000 www-data

#change the web_root to laravel /var/www/html/public folder
RUN sed -i -e "s/html/html\/public/g" /etc/apache2/sites-enabled/000-default.conf

# enable apache module rewrite
RUN a2enmod rewrite

#copy source files and run composer
COPY . $APP_HOME

# install all PHP dependencies
RUN composer install --no-interaction

RUN php artisan key:generate

#change ownership of our applications
RUN chown -R www-data:www-data $APP_HOME
```

## References
- [Deploying your Laravel/PHP applications in production using Docker](https://blog.cloud66.com/deploying-your-laravel-php-applications-with-cloud-66/)