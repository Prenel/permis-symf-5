# Utiliser une image PHP 8.2 FPM basée sur Alpine
FROM php:8.2-fpm-alpine

# Installer les dépendances nécessaires
RUN apk update && apk add --no-cache bash icu-dev git unzip vim mysql-client postgresql-dev \
    && docker-php-ext-install intl pdo pdo_pgsql pdo_mysql


# Installer Composer
COPY --from=composer:2.6 /usr/bin/composer /usr/bin/composer

# Définir le répertoire de travail
WORKDIR /var/www/html

COPY ../vendor /var/www/html/vendor/

# Donner les permissions à www-data pour Symfony
RUN chown -R www-data:www-data /var/www/html

# Exposer le port par défaut de PHP-FPM
EXPOSE 4000

CMD ["tail", "-f", "/dev/null"]
