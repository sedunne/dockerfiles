FROM alpine:latest 

LABEL org.opencontainers.image.title='sedunne/figlet'
LABEL org.opencontainers.image.description='figlet on minideb'
LABEL org.opencontainers.image.url='https://github.com/sedunne/dockerfiles'
LABEL org.opencontainers.image.authors='Stephen Dunne <stephen@f914.net>'

RUN apk --no-cache add figlet

ENTRYPOINT ["figlet"]
