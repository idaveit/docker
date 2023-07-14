FROM httpd:2.4-alpine

ARG TARGETARCH
RUN echo "I'm building for $TARGETARCH"
RUN apk add --update mariadb-dev make gcc musl-dev apr apr-dev apr-util-dev apr-util automake autoconf
RUN mkdir -p /usr/local/src/mod_auth_cookie_mysql2
RUN mkdir -p /usr/local/src/cronolog
COPY mod_auth_cookie_mysql2/* /usr/local/src/mod_auth_cookie_mysql2/
COPY cronolog/. /usr/local/src/cronolog/
RUN ln -sf /usr/bin/aclocal /usr/bin/aclocal-1.13
RUN ln -sf /usr/bin/automake /usr/bin/automake-1.13
WORKDIR /usr/local/src/mod_auth_cookie_mysql2
RUN make
RUN make install
WORKDIR /usr/local/src/cronolog
RUN ls -al src
RUN if [ $TARGETARCH == 'amd64' ]; then echo "running ./configure --build=x86_64-unknown-linux-gnu"; elif [ $BUILDARCH == 'arm64' ]; then echo "running ./configure --build=aarch64-unknown-linux-gnu"; else echo "running ./configure"; fi
RUN if [ $TARGETARCH == 'amd64' ]; then ./configure --build=x86_64-unknown-linux-gnu; elif [ $BUILDARCH == 'arm64' ]; then ./configure --build=aarch64-unknown-linux-gnu; else ./configure; fi
RUN make
RUN make install
RUN rm -rf /usr/bin/aclocal-1.13 /usr/bin/automake-1.13
RUN apk del mariadb-dev make gcc musl-dev apache2-dev apr apr-dev apr-util-dev apr-util automake autoconf
