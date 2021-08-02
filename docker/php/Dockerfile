FROM docker.io/bitnami/php-fpm:7.4-debian-10

RUN echo "opcache.revalidate_freq = 0" >> /opt/bitnami/php/etc/php.ini

RUN apt-get update
RUN apt-get install -y nano

ARG PUID=1000
ENV PUID ${PUID}

ARG PGID=1000
ENV PGID ${PGID}

RUN chmod -R 0777 /opt/bitnami

RUN groupadd -g 1001 bitnami
RUN useradd -u 1001 -g bitnami -m bitnami
RUN usermod -p "*" bitnami -s /bin/bash

RUN groupadd -g ${PGID} developer
RUN useradd -u ${PUID} -g developer -m developer -G bitnami
RUN usermod -p "*" developer -s /bin/bash

RUN chown ${PUID}:${PGID} /app

USER ${PUID}:${PGID}

RUN composer create-project wintercms/winter /app
#RUN php artisan winter:install

EXPOSE 9000
