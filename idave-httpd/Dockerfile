FROM httpd:2.4-alpine

RUN apk add --update mariadb-dev make gcc musl-dev apr apr-dev apr-util-dev apr-util automake
RUN mkdir -p /usr/local/src/mod_auth_cookie_mysql2
RUN mkdir -p /usr/local/src/cronolog
COPY mod_auth_cookie_mysql2/* /usr/local/src/mod_auth_cookie_mysql2/
COPY cronolog/. /usr/local/src/cronolog/
WORKDIR /usr/local/src/mod_auth_cookie_mysql2
RUN make
RUN make install
WORKDIR /usr/local/src/cronolog
RUN ls -al src
RUN ./configure
RUN make
RUN make install
RUN apk del mariadb-dev make gcc musl-dev apache2-dev apr apr-dev apr-util-dev apr-util automake
