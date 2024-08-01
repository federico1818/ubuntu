FROM php:8.3.9-fpm

# Arguments defined in docker-compose.yml
ARG user

# Install system dependencies
RUN apt-get update && apt-get install -y \
    git \
    curl \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    libzip-dev \
    libcurl4-openssl-dev \
    zip \
    unzip

# Install REDIS extension
# RUN pecl install -o -f redis \
#    &&  rm -rf /tmp/pear \
#    &&  docker-php-ext-enable redis

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Install PHP extensions
RUN docker-php-ext-install ctype curl dom fileinfo filter mbstring pdo_mysql xml

# Get latest Composer
COPY --from=composer:2.7.7 /usr/bin/composer /usr/bin/composer

# Create system user to run Composer and Artisan Commands
RUN useradd -G www-data,root -u 1000 -d /home/${user} ${user}
RUN mkdir -p /home/$user/.composer && \
    chown -R $user:$user /home/${user}

# Set working directory
WORKDIR /var/www

USER ${user}