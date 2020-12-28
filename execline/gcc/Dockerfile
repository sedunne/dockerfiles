## https://skarnet.org/software/execline/
FROM gcc:10 as build-execline
WORKDIR /build
ENV EXECLINE_VERSION=2.6.1.1

## this is somehow easier than trying to do it sanely inside the container with RUN
COPY --from=sedunne/skalibs:gcc /build/artifacts/ /
RUN ldconfig -v

RUN wget -q https://skarnet.org/software/execline/execline-${EXECLINE_VERSION}.tar.gz && \
    tar -xf execline-${EXECLINE_VERSION}.tar.gz && cd execline-${EXECLINE_VERSION} && \
    ./configure --enable-shared --disable-static --disable-allstatic \
        --libexecdir=/lib/execline --with-dynlib=/lib --bindir=/lib/execline/bin --enable-absolute-paths && \
    make && DESTDIR=/build/artifacts/ make install && \
    rm -rf /build/execline*
