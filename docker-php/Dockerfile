FROM php:8.1.10-fpm

RUN docker-php-source extract \
	&& docker-php-source delete

RUN apt-get update && apt-get install -y \
		libfreetype6-dev \
		libjpeg62-turbo-dev \
		libpng-dev \
	&& docker-php-ext-configure gd --with-freetype --with-jpeg \
	&& docker-php-ext-install -j$(nproc) gd

WORKDIR /var/www/app

COPY ./../ ./

EXPOSE 9000

CMD ["php-fpm"]
