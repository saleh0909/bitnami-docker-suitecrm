FROM bitnami/oraclelinux-extras:7-r3
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages bzip2-libs cronie cyrus-sasl-lib expat freetype glibc gmp keyutils-libs krb5-libs libcom_err libcurl libgcc libgcrypt libgpg-error libicu libidn libjpeg-turbo libpng libselinux libssh2 libstdc++ libxml2 libxslt ncurses-libs nspr nss nss-softokn-freebl nss-util openldap openssl-libs pcre postgresql-libs readline sqlite xz-libs zlib
RUN bitnami-pkg unpack apache-2.4.33-3 --checksum 0611709446389dbf1b9a08ee4b8b447443e356e286a9c6dee312d55f72e465d6
RUN bitnami-pkg unpack php-7.0.30-3 --checksum 1de72790ae78f941b400212bba9f04201373b7573e679818a7f06edbb65cf473
RUN bitnami-pkg unpack mysql-client-10.1.33-0 --checksum 250e5cd0f6f256fb39e8d8b703856dbc0257f3da9659b8565398173a3119dd9c
RUN bitnami-pkg install libphp-7.0.30-6 --checksum 31cf8fe7e06aee8a9954e5205b9d49e7ec8c8eef4d260a9ed21e1955ec10a9f9
RUN bitnami-pkg unpack suitecrm-7.10.4-2 --checksum 6ab7010aa34f64c279bdf50cdc1449bf14a29421053b7bd602864b747ef96afd

COPY rootfs /
ENV ALLOW_EMPTY_PASSWORD="no" \
    APACHE_HTTPS_PORT_NUMBER="443" \
    APACHE_HTTP_PORT_NUMBER="80" \
    BITNAMI_APP_NAME="suitecrm" \
    BITNAMI_IMAGE_VERSION="7.10.4-ol-7-r0" \
    MARIADB_HOST="mariadb" \
    MARIADB_PORT_NUMBER="3306" \
    MARIADB_ROOT_PASSWORD="" \
    MARIADB_ROOT_USER="root" \
    MYSQL_CLIENT_CREATE_DATABASE_NAME="" \
    MYSQL_CLIENT_CREATE_DATABASE_PASSWORD="" \
    MYSQL_CLIENT_CREATE_DATABASE_PRIVILEGES="ALL" \
    MYSQL_CLIENT_CREATE_DATABASE_USER="" \
    PATH="/opt/bitnami/apache/bin:/opt/bitnami/php/bin:/opt/bitnami/mysql/bin:$PATH" \
    SUITECRM_DATABASE_NAME="bitnami_<<name>>" \
    SUITECRM_DATABASE_PASSWORD="" \
    SUITECRM_DATABASE_USER="bn_<<name>>" \
    SUITECRM_EMAIL="user@example.com" \
    SUITECRM_HOST="127.0.0.1" \
    SUITECRM_HTTP_TIMEOUT="120" \
    SUITECRM_LAST_NAME="Name" \
    SUITECRM_PASSWORD="bitnami" \
    SUITECRM_SMTP_HOST="" \
    SUITECRM_SMTP_PASSWORD="" \
    SUITECRM_SMTP_PORT="" \
    SUITECRM_SMTP_PROTOCOL="" \
    SUITECRM_SMTP_USER="" \
    SUITECRM_USERNAME="user"

EXPOSE 80 443

ENTRYPOINT ["/app-entrypoint.sh"]
CMD ["/run.sh"]