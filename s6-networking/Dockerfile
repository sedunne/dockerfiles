# https://skarnet.org/software/s6-networking/
FROM bitnami/minideb:buster as run-s6-networking

COPY --from=sedunne/skalibs:gcc /build/artifacts/ /
COPY --from=sedunne/execline:gcc /build/artifacts/ /
COPY --from=sedunne/s6:gcc /build/artifacts/ /
COPY --from=sedunne/s6-dns:gcc /build/artifacts/ /
COPY --from=sedunne/s6-networking:gcc /build/artifacts/ /
RUN ldconfig -v

CMD [ "/bin/s6-tcpserver" ]
