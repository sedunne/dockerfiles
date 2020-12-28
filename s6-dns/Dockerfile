FROM bitnami/minideb:buster

COPY --from=sedunne/skalibs:gcc /build/artifacts/ /
COPY --from=sedunne/s6-dns:gcc /build/artifacts/ /
RUN ldconfig -v

CMD [ "/bin/s6-dnsip" ]
