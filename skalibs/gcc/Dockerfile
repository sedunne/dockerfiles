## https://skarnet.org/software/skalibs/
FROM gcc:10 as build-skalibs
WORKDIR /build
ENV SKALIBS_VERSION=2.9.3.0

RUN wget -q https://skarnet.org/software/skalibs/skalibs-${SKALIBS_VERSION}.tar.gz && \
    tar -xf skalibs-${SKALIBS_VERSION}.tar.gz && cd skalibs-${SKALIBS_VERSION} && \
    ./configure --enable-shared --disable-static --disable-allstatic --libexecdir=/lib/skalibs --with-dynlib=/lib && \
    make && DESTDIR=/build/artifacts/ make install && \
    rm -rf /build/skalibs*
