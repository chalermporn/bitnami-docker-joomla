FROM bitnami/oraclelinux-extras:7-r23
LABEL maintainer "Bitnami <containers@bitnami.com>"

# Install required system packages and dependencies
RUN install_packages bzip2-libs cyrus-sasl-lib expat freetds freetype glibc gmp gnutls keyutils-libs krb5-libs libcom_err libcurl libffi libgcc libgcrypt libgpg-error libicu libidn libjpeg-turbo libmcrypt libpng libselinux libssh2 libstdc++ libtasn1 libtidy libxml2 libxslt ncurses-libs nettle nspr nss nss-softokn-freebl nss-util openldap openssl-libs p11-kit pcre postgresql-libs readline sqlite xz-libs zlib
RUN bitnami-pkg unpack apache-2.4.33-4 --checksum 4e8daac4fc3f70870a856be2dbabe35c060bae4319da105a1cd38ea2335cc5a1
RUN bitnami-pkg unpack php-7.0.30-7 --checksum 5754714c3964c1ced5ed1d9c8c3f059ca59f65c400f1c9e00f655bae869bef61
RUN bitnami-pkg unpack mysql-client-10.1.34-0 --checksum 012f1f222898565b55f7d4522514c7c130d2bfe4c988754eed658ef6dafa980c
RUN bitnami-pkg install libphp-7.0.30-8 --checksum d56f04ce65e0caabe624739aa5a1b4d0980b612edc5331b647c86457b1bc36e6
RUN bitnami-pkg unpack joomla-3.8.10-0 --checksum 56da2f666fbe010c889c6412a89ad6d2142161b1c804d90f6c335ff0956fa523

COPY rootfs /
ENV ALLOW_EMPTY_PASSWORD="no" \
    APACHE_HTTPS_PORT_NUMBER="443" \
    APACHE_HTTP_PORT_NUMBER="80" \
    BITNAMI_APP_NAME="joomla" \
    BITNAMI_IMAGE_VERSION="3.8.10-ol-7-r5" \
    JOOMLA_DATABASE_NAME="bitnami_joomla" \
    JOOMLA_DATABASE_PASSWORD="" \
    JOOMLA_DATABASE_USER="bn_joomla" \
    JOOMLA_EMAIL="user@example.com" \
    JOOMLA_FIRST_NAME="User" \
    JOOMLA_LAST_NAME="Name" \
    JOOMLA_PASSWORD="bitnami" \
    JOOMLA_USERNAME="user" \
    MARIADB_HOST="mariadb" \
    MARIADB_PORT_NUMBER="3306" \
    MARIADB_ROOT_PASSWORD="" \
    MARIADB_ROOT_USER="root" \
    MYSQL_CLIENT_CREATE_DATABASE_NAME="" \
    MYSQL_CLIENT_CREATE_DATABASE_PASSWORD="" \
    MYSQL_CLIENT_CREATE_DATABASE_PRIVILEGES="ALL" \
    MYSQL_CLIENT_CREATE_DATABASE_USER="" \
    PATH="/opt/bitnami/apache/bin:/opt/bitnami/php/bin:/opt/bitnami/mysql/bin:/opt/bitnami/joomla/bin:$PATH" \
    SMTP_HOST="" \
    SMTP_PASSWORD="" \
    SMTP_PORT="" \
    SMTP_PROTOCOL="tls" \
    SMTP_USER=""

EXPOSE 80 443

ENTRYPOINT ["/app-entrypoint.sh"]
CMD ["nami","start","--foreground","apache"]