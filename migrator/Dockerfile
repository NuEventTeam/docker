FROM golang:1.21.6-alpine3.18 AS builder
WORKDIR /app

COPY ../../migration .

RUN go  build -v -ldflags="-w -s" -o app main.go

FROM alpine:3.18
WORKDIR /app

COPY --from=builder /app .

ENTRYPOINT ["app", "migrate", "up"]
