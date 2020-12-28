## https://skarnet.org/software/s6-dns/
FROM gcc:10 as build-s6-dns
WORKDIR /build
ENV S6DNS_VERSION=2.3.3.0

COPY --from=sedunne/skalibs:gcc /build/artifacts/ /
COPY --from=sedunne/execline:gcc /build/artifacts/ /
COPY --from=sedunne/s6:gcc /build/artifacts/ /
RUN ldconfig -v

RUN wget -q https://skarnet.org/software/s6-dns/s6-dns-${S6DNS_VERSION}.tar.gz && \
    tar -xf s6-dns-${S6DNS_VERSION}.tar.gz && cd s6-dns-${S6DNS_VERSION} && \
    ./configure --enable-shared --disable-static --disable-allstatic \
        --libexecdir=/lib/s6-dns --with-dynlib=/lib --bindir=/bin --enable-absolute-paths && \
    make && DESTDIR=/build/artifacts/ make install && \
    rm -rf /build/s6-dns*
