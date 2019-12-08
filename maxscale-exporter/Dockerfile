FROM golang:1.13-alpine

RUN apk add git
WORKDIR /app

ENV SRC_DIR=/app/

RUN go get github.com/buger/jsonparser \
    && go get github.com/prometheus/client_golang/prometheus \
    && go get github.com/prometheus/client_golang/prometheus/promhttp

COPY maxscale_exporter.go ./

RUN go build -o maxscale_exporter; \
    mv maxscale_exporter /go/bin

CMD  ["maxscale_exporter", "-address", "admin:mariadb@maxscale:8989"]

EXPOSE 9195
