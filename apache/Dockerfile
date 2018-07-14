FROM httpd:2.4.33

ARG UID=33
ARG GID=33

# Thanks Adam :)
RUN usermod -u $UID www-data \
    && groupmod -g $GID www-data \
    && echo "IncludeOptional conf.d/*.conf" >> /usr/local/apache2/conf/httpd.conf
