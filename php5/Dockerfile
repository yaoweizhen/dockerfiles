FROM php:5-fpm
RUN apt-get update && apt-get install -y \
      libfreetype6-dev \
      libjpeg62-turbo-dev \
      libmcrypt-dev \
      libpng12-dev \
      && docker-php-ext-install -j$(nproc) iconv mcrypt pdo_mysql \
      && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
      && docker-php-ext-install -j$(nproc) gd
WORKDIR /root
RUN apt-get install -y git unzip vim mysql-client
#RUN apt-get install -y wget
#RUN wget https://github.com/drush-ops/drush/archive/7.3.0.tar.gz
#RUN tar zxf 7.3.0.tar.gz
#RUN ln -s /root/drush-7.3.0/drush /usr/local/bin/drush
#RUN chmod a+x /usr/local/bin/drush
#RUN rm /root/7.3.0.tar.gz

#RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
#RUN php -r "if (hash_file('SHA384', 'composer-setup.php') === \
#      'e115a8dc7871f15d853148a7fbac7da27d6c0030b848d9b3dc09e2a0388afed865e6a3d6b3c0fad45c48e2b5fc1196ae') \
#      { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
#RUN php composer-setup.php
#RUN php -r "unlink('composer-setup.php');"
#RUN mv composer.phar /usr/local/bin/composer
#RUN composer global require drush/drush:7.3
#ENV PATH /root/.composer/vendor/bin:$PATH

RUN php -r "readfile('http://files.drush.org/drush.phar');" > drush.phar
RUN chmod +x drush.phar
RUN mv drush.phar /usr/local/bin
#RUN drush.phar --version

ADD . /php5
#WORKDIR /php5
