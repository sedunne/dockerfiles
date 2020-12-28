# https://skarnet.org/software/s6-networking/
FROM sedunne/libressl:gcc as build-s6-networking
WORKDIR /build
ENV S6NETWORKING_VERSION=2.3.2.0

COPY --from=sedunne/skalibs:gcc /build/artifacts/ /
COPY --from=sedunne/execline:gcc /build/artifacts/ /
COPY --from=sedunne/s6:gcc /build/artifacts/ /
COPY --from=sedunne/s6-dns:gcc /build/artifacts/ /
RUN ldconfig -v

RUN wget -q https://skarnet.org/software/s6-networking/s6-networking-${S6NETWORKING_VERSION}.tar.gz && \
    tar -xf s6-networking-${S6NETWORKING_VERSION}.tar.gz && cd s6-networking-${S6NETWORKING_VERSION} && \
    ./configure --enable-shared --disable-static --disable-allstatic \
        --libexecdir=/lib/s6-networking --with-dynlib=/lib --bindir=/bin --enable-ssl=libressl --with-ssl-path=/usr/local && \
    make && DESTDIR=/build/artifacts/ make install && \
    rm -rf /build/s6-networking*

