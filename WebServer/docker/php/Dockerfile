# docker/php/Dockerfile
FROM php:8.2-fpm

# Create and configure APT resources
RUN mkdir -p /etc/apt && \
    echo "deb http://deb.debian.org/debian bullseye main" > /etc/apt/sources.list && \
    echo "deb http://security.debian.org/debian-security bullseye-security main" >> /etc/apt/sources.list && \
    echo "deb http://deb.debian.org/debian bullseye-updates main" >> /etc/apt/sources.list

# Perform package installations
RUN apt-get update && \
    apt-get install -y \
    git \
    curl \
    wget \
    zip \
    unzip \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Install PHP extensions
RUN docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd

# Install Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/html

RUN usermod -u 1000 www-data

CMD ["php-fpm"]
EXPOSE 9000
