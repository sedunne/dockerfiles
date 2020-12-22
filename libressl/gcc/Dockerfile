FROM gcc:10 as buildtime
WORKDIR /build
ENV VERSION=3.1.5

RUN wget -q https://ftp.openbsd.org/pub/OpenBSD/LibreSSL/libressl-${VERSION}.tar.gz && \
    tar -xf libressl-${VERSION}.tar.gz && cd libressl-${VERSION}/ && \
    ./configure && make check && DESTDIR=/build/artifacts make install && \
    rm -rf /build/libressl*

FROM gcc:10 as runtime
ENV VERSION=3.1.5

LABEL org.opencontainers.image.title='sedunne/libressl:gcc'
LABEL org.opencontainers.image.description='Rebuild of upstream gcc with LibreSSL libraries.'
LABEL org.opencontainers.image.url='https://github.com/sedunne/dockerfiles'
LABEL org.opencontainers.image.authors='Stephen Dunne <stephen@f914.net>'
LABEL org.opencontainers.image.version=${VERSION}

COPY --from=buildtime /build/artifacts/usr/local/ /usr/local/
RUN ldconfig -v
