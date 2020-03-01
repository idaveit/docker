FROM httpd:2.4-alpine

RUN apk add --update mariadb-dev make gcc musl-dev apache2-dev
RUN mkdir -p /usr/local/src/mod_auth_cookie_mysql2
WORKDIR /usr/local/src/mod_auth_cookie_mysql2
COPY mod_auth_cookie_mysql2/* /usr/local/src/mod_auth_cookie_mysql2/
RUN make
RUN make install
RUN apk del mariadb-dev make gcc musl-dev apache2-dev
