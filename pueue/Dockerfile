## pueue
FROM debian:bullseye

EXPOSE 6924/tcp

ENV PUEUE_VERSION="v1.0.3"
WORKDIR /etc/pueue

## add server
ADD https://github.com/Nukesor/pueue/releases/download/${PUEUE_VERSION}/pueued-linux-x86_64 /usr/local/bin/pueued

## add client
ADD https://github.com/Nukesor/pueue/releases/download/${PUEUE_VERSION}/pueue-linux-x86_64 /usr/local/bin/pueue

RUN chmod +x /usr/local/bin/pueue ; chmod +x /usr/local/bin/pueued

COPY pueue.yml /etc/pueue/pueue.yml

CMD ["pueued", "-vv"]
