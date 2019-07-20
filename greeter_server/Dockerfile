FROM golang:1.11.12-alpine AS build_base

WORKDIR /go/src/github.com/zerofruit/hello-grpc/greeter_server

COPY . ./

RUN apk --no-cache --virtual add \
    git \
    curl \
    g++ \
    gcc \
    && export GO111MODULE=on \
    && go mod vendor \
    && go install /go/src/github.com/zerofruit/hello-grpc/greeter_server

FROM alpine:3.9

COPY --from=build_base /go/bin/greeter_server /

EXPOSE 50051
ENTRYPOINT ["/greeter_server"]




