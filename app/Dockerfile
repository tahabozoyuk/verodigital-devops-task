FROM php:8.1-apache

RUN apt-get update && apt-get install -y gnupg2
RUN curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -
RUN curl https://packages.microsoft.com/config/ubuntu/20.04/prod.list > /etc/apt/sources.list.d/mssql-release.list
RUN apt-get update
RUN ACCEPT_EULA=Y apt-get install -y msodbcsql18 mssql-tools18
RUN apt-get update && apt-get install -y unixodbc-dev
RUN pecl install pdo_sqlsrv sqlsrv
RUN docker-php-ext-enable pdo_sqlsrv sqlsrv

COPY . /var/www/html/

CMD ["apache2-foreground"]

