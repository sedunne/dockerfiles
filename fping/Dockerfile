FROM gcc:10 as buildtime
WORKDIR /build
ENV VERSION=5.0

RUN wget -q https://github.com/schweikert/fping/releases/download/v${VERSION}/fping-${VERSION}.tar.gz && \
    tar -xf fping-${VERSION}.tar.gz && \
    cd fping-${VERSION}/ && \
    ./configure \
        --prefix=/usr \
        --mandir=/usr/share/man && \
    DESTDIR=/build/artifacts make install && cd /build && \
    rm -rf /build/fping*


FROM bitnami/minideb:buster as runtime
ENV VERSION=5.0

LABEL org.opencontainers.image.title='sedunne/fping'
LABEL org.opencontainers.image.description='fping on minideb'
LABEL org.opencontainers.image.url='https://github.com/sedunne/dockerfiles'
LABEL org.opencontainers.image.authors='Stephen Dunne <stephen@f914.net>'
LABEL org.opencontainers.image.version=${VERSION}

COPY --from=buildtime /build/artifacts/ /

CMD [ "/usr/sbin/fping", "--version" ]
