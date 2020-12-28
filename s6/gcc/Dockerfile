## https://skarnet.org/software/s6/
FROM gcc:10 as build-s6
WORKDIR /build
ENV S6_VERSION=2.9.2.0

## this is somehow easier than trying to do it sanely inside the container with RUN
COPY --from=sedunne/skalibs:gcc /build/artifacts/ /
COPY --from=sedunne/execline:gcc /build/artifacts/ /
RUN ldconfig -v

RUN wget -q https://skarnet.org/software/s6/s6-${S6_VERSION}.tar.gz && \
    tar -xf s6-${S6_VERSION}.tar.gz && cd s6-${S6_VERSION} && \
    ./configure --enable-shared --disable-static --disable-allstatic \
        --libexecdir=/lib/s6 --with-dynlib=/lib --bindir=/bin --enable-absolute-paths && \
    make && DESTDIR=/build/artifacts/ make install && \
    rm -rf /build/s6*
