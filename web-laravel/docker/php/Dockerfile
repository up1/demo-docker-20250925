FROM php:8.3-fpm-alpine


# System deps
RUN apk add --no-cache \
bash curl git unzip icu-dev oniguruma-dev libzip-dev libpng-dev \
freetype-dev libjpeg-turbo-dev \
libxml2-dev


# PHP extensions commonly needed by Laravel
RUN docker-php-ext-configure gd \
--with-freetype \
--with-jpeg \
&& docker-php-ext-install -j"$(nproc)" \
bcmath intl mbstring pdo pdo_mysql zip gd xml opcache


# Opcache recommended settings (can be tuned per env)
RUN { \
echo "opcache.enable=1"; \
echo "opcache.enable_cli=1"; \
echo "opcache.memory_consumption=128"; \
echo "opcache.interned_strings_buffer=16"; \
echo "opcache.max_accelerated_files=10000"; \
echo "opcache.validate_timestamps=1"; \
echo "opcache.revalidate_freq=0"; \
} > /usr/local/etc/php/conf.d/opcache.ini


# Set working dir
WORKDIR /var/www/html

# www-data UID tweak (optional) to avoid permission issues on some hosts
# ARG PUID=1000
# RUN adduser -D -u ${PUID} www
# USER www