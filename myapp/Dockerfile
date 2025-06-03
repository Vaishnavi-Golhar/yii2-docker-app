# Use official PHP 8.0 Apache base image
FROM php:8.0-apache

# Install system dependencies and PHP extensions needed by Yii2
RUN apt-get update && apt-get install -y \
    libonig-dev \
    libzip-dev \
    zip \
    unzip \
    && docker-php-ext-install pdo pdo_mysql mbstring zip \
    && a2enmod rewrite \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Copy application source code to Apache web root
COPY . /var/www/html/

# Set working directory
WORKDIR /var/www/html

# Set proper permissions for runtime and assets directories
RUN chmod -R 777 runtime web/assets

# Expose port 80 for Apache
EXPOSE 80
