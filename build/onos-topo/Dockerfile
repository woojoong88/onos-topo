FROM onosproject/golang-build:v0.6.3 as build

ENV GO111MODULE=on
COPY . /go/src/github.com/onosproject/onos-topo
RUN cd /go/src/github.com/onosproject/onos-topo && GOFLAGS=-mod=vendor make build

FROM alpine:3.11
RUN apk add libc6-compat

USER nobody

COPY --from=build /go/src/github.com/onosproject/onos-topo/build/_output/onos-topo /usr/local/bin/onos-topo

ENTRYPOINT ["onos-topo"]
