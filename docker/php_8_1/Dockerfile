# Базовый образ
FROM php:8.1-fpm

# Обновляем систему и устанавливаем необходимые зависимости
RUN apt-get update && apt-get install -y \
    curl \
    git \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libzip-dev \
    && docker-php-ext-install pdo pdo_mysql \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install gd zip

# Установка Xdebug
RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

# Добавляем настройки для Xdebug (например, для дебага)
# RUN echo "zend_extension=$(find /usr/local/lib/php/extensions -name xdebug.so)" > /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
#     && echo "xdebug.start_with_request=yes" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
#     && echo "xdebug.mode=debug" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
#     && echo "xdebug.client_host=host.docker.internal" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
#     && echo "xdebug.client_port=9003" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
#     && echo "xdebug.log=/var/log/xdebug/xdebug.log" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
#     && echo "xdebug.remote_connect_back = 1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

# Устанавливаем Composer
# RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Устанавливаем рабочую директорию
WORKDIR /var/www/test-modx

# Стартуем PHP-FPM
ENTRYPOINT [ "php-fpm" ]
