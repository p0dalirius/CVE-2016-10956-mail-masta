FROM debian:latest

ENV WPVERSION=5.5.3

ENV APACHE_DOCUMENT_ROOT /var/www/
ENV DEBIAN_FRONTEND=noninteractive
RUN apt -y -qq update ;\
    apt -y -qq install wget apache2 php zip unzip

RUN \
    rm -rf /var/www/html/; \
    mkdir -p ${APACHE_DOCUMENT_ROOT} ;\
    printf "<VirtualHost *:${HTTP_PORT}>\nServerAdmin webmaster@localhost\n#ServerName localhost\nServerAlias localhost\nDocumentRoot ${APACHE_DOCUMENT_ROOT}/wordpress\nErrorLog \${APACHE_LOG_DIR}/error.log\nCustomLog \${APACHE_LOG_DIR}/access.log combined\n</VirtualHost>\n" \
    > /etc/apache2/sites-available/000-default.conf;


RUN cd ${APACHE_DOCUMENT_ROOT} ; rm -rf * ;\
    wget https://wordpress.org/wordpress-${WPVERSION}.zip ;\
    unzip wordpress-${WPVERSION}.zip ;\
    chown -R www-data:www-data ${APACHE_DOCUMENT_ROOT}/wordpress

CMD ["apachectl","-D","FOREGROUND"]
