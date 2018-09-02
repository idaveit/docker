FROM httpd:alpine

RUN apk add --update mariadb-client mariadb-client-libs make gcc mysql-dev musl-dev
RUN mkdir -p /usr/local/src/mod_auth_cookie_mysql2
WORKDIR /usr/local/src/mod_auth_cookie_mysql2
COPY mod_auth_cookie_mysql2/* /usr/local/src/mod_auth_cookie_mysql2/
RUN make
RUN make install
RUN apk del make gcc mysql-dev musl-dev