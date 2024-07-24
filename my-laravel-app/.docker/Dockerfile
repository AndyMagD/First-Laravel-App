# Use the official PHP Apache image from Docker Hub
FROM php:8.3-apache

# Set working directory inside the container
WORKDIR /var/www/html

# Install PHP extensions and other dependencies
RUN apt-get update && apt-get install -y \
    libzip-dev \
    zip \
    && docker-php-ext-install pdo_mysql zip

COPY apache2/apache2.conf /etc/apache2
COPY apache2/000-default.conf /etc/apache2/sites-enabled/
RUN a2enmod rewrite


# Copy composer.lock and composer.json to optimize Docker caching
# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Expose port 80 and start Apache
EXPOSE 80
