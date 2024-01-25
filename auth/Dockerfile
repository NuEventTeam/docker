FROM golang:1.21.6-alpine3.18 AS builder
WORKDIR /app

RUN apk add --no-cache tzdata
RUN apk add git

COPY ../../sso .

RUN go  build -v -ldflags="-w -s" -o app ./cmd/main.go

FROM alpine:3.18
WORKDIR /app

COPY --from=builder /usr/share/zoneinfo /usr/share/zoneinfo


ENV TZ=Asia/Almaty

COPY --from=builder /app .

CMD ["sh", "-c", "./app"]
