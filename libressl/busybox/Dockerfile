FROM gcc:10 as buildtime
WORKDIR /build
ENV VERSION=3.1.5

RUN wget -q https://ftp.openbsd.org/pub/OpenBSD/LibreSSL/libressl-${VERSION}.tar.gz && \
    tar -xf libressl-${VERSION}.tar.gz && cd libressl-${VERSION}/ && \
    ./configure --prefix=/ && DESTDIR=/build/artifacts make install && \
    rm -rf /build/libressl*


FROM busybox:glibc as runtime 
ENV VERSION=3.1.5

LABEL org.opencontainers.image.title='sedunne/libressl:3.1'
LABEL org.opencontainers.image.description='Busybox with LibreSSL.'
LABEL org.opencontainers.image.url='https://github.com/sedunne/dockerfiles'
LABEL org.opencontainers.image.authors='Stephen Dunne <stephen@f914.net>'
LABEL org.opencontainers.image.version=${VERSION}

COPY --from=buildtime /build/artifacts/ /

CMD [ "/bin/openssl", "version" ]
