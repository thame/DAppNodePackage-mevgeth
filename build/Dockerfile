# Build Geth in a stock Go builder container
FROM golang:1.16-alpine as builder

ARG UPSTREAM_VERSION

RUN apk add --no-cache make gcc musl-dev linux-headers git bash

RUN git clone -b ${UPSTREAM_VERSION} https://github.com/flashbots/mev-geth.git && \
    cd mev-geth && make geth
    
# Pull Geth into a second stage deploy alpine container
FROM alpine:latest

RUN apk add --no-cache ca-certificates

COPY --from=builder /go/mev-geth/build/bin/geth /usr/local/bin/

ENTRYPOINT geth --http --http.addr 0.0.0.0 --http.corsdomain "*" --http.vhosts "*" --ws --ws.origins "*" --ws.addr 0.0.0.0 --syncmode ${SYNCMODE:-fast} --metrics --metrics.addr 0.0.0.0 $EXTRA_OPTIONS
