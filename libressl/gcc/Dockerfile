FROM gcc:10

LABEL org.opencontainers.image.title='sedunne/libressl:gcc'
LABEL org.opencontainers.image.description='Rebuild of upstream gcc with LibreSSL libraries.'
LABEL org.opencontainers.image.url='https://github.com/sedunne/dockerfiles'
LABEL org.opencontainers.image.authors='Stephen Dunne <stephen@f914.net>'

WORKDIR /build
ENV VERSION=3.1.5

RUN wget -q https://ftp.openbsd.org/pub/OpenBSD/LibreSSL/libressl-${VERSION}.tar.gz && \
    tar -xf libressl-${VERSION}.tar.gz && cd libressl-${VERSION}/ && \
    ./configure && make check && make install && ldconfig -v && rm -rf /build/*

CMD [ "/usr/local/bin/openssl", "version" ]
