ARG PHPFPM_VERSION
FROM php:${PHPFPM_VERSION}-fpm

COPY ./php.ini /usr/local/etc/php/

# BASE
RUN apt -y update
RUN apt install -y zip unzip libxrender1 libfontconfig libxext-dev libzip-dev
RUN docker-php-ext-install pdo_mysql zip

# GD
RUN apt install -y libfreetype6-dev libjpeg62-turbo-dev libpng-dev libjpeg-dev
RUN docker-php-ext-configure gd --with-freetype=/usr/include --with-jpeg=/usr/include
RUN docker-php-ext-install -j$(nproc) gd

# COMPOSER
ARG COMPOSER_VERSION
RUN curl -sS https://getcomposer.org/installer | php -- --version=${COMPOSER_VERSION}
RUN mv composer.phar /usr/bin/composer

# NODE
ARG NODEJS_VERSION_MAJOR
RUN curl -fsSL https://deb.nodesource.com/setup_${NODEJS_VERSION_MAJOR} | bash -
RUN apt install -y nodejs
RUN rm -rf /var/lib/apt/lists/

# NPM
RUN npm install -g yarn
