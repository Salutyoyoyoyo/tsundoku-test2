FROM php:8.2-fpm

# Installer des dépendances système
RUN apt-get update && apt-get install -y \
    libfreetype-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    git \
    unzip \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd

# Installer Composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php composer-setup.php --install-dir=/usr/local/bin --filename=composer \
    && php -r "unlink('composer-setup.php');"

WORKDIR /var/www/

COPY docker .

# Copier le fichier composer.json et composer.lock s'ils existent
COPY composer.json composer.lock ./

# Installer les dépendances de Composer
RUN composer install --no-scripts --no-autoloader

# Copier le reste du code de l'application
COPY . .

# Générer l'autoloader
RUN composer dump-autoload --optimize

EXPOSE 9000

CMD ["php-fpm"]