ARG PHPFPM_VERSION
FROM php:${PHPFPM_VERSION}-fpm

COPY ./php.ini /usr/local/etc/php/

RUN apt -y update
RUN apt install -y zip unzip libxrender1 libfontconfig libxext-dev libzip-dev
RUN docker-php-ext-install pdo_mysql zip

ARG COMPOSER_VERSION
RUN curl -sS https://getcomposer.org/installer | php -- --version=${COMPOSER_VERSION}
RUN mv composer.phar /usr/bin/composer

ARG NODEJS_VERSION_MAJOR
RUN curl -fsSL https://deb.nodesource.com/setup_${NODEJS_VERSION_MAJOR} | bash -
RUN apt install -y nodejs
RUN rm -rf /var/lib/apt/lists/

# yarn install
RUN npm install -g yarn
