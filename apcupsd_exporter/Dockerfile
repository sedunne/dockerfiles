## clone the source from github to a subdir called 'src'
FROM golang:bullseye

EXPOSE 9162/tcp

WORKDIR /go/src/apcupsd_exporter
COPY src/ .

RUN go get -d -v .
RUN go install -v ./cmd/apcupsd_exporter/

ENTRYPOINT ["apcupsd_exporter"]
CMD ["-h"]
