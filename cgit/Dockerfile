FROM httpd:2.4-alpine as runtime

LABEL org.opencontainers.image.title='sedunne/cgit'
LABEL org.opencontainers.image.description='cgit on httpd-alpine'
LABEL org.opencontainers.image.url='https://github.com/sedunne/dockerfiles'
LABEL org.opencontainers.image.authors='Stephen Dunne <stephen@f914.net>'

WORKDIR '/srv/git'

RUN apk add --no-cache git cgit
COPY httpd.conf /usr/local/apache2/conf/httpd.conf
COPY cgitrc /etc/cgitrc

## by default apache runs as the 'daemon' user/group in the alpine image
## this can probably be reworked to be better, but since using chown w/ADD doesn't behave
##  like most people expect, you have to get a little messy if we're not just pulling the tar from the web
COPY docker-cgit-test.tar.gz /srv/git/
RUN tar xf docker-cgit-test.tar.gz \
  && chown -R daemon.daemon docker-cgit-test.git \
  && rm -f docker-cgit-test.tar.gz

EXPOSE 80
CMD ["httpd-foreground"]
