FROM golang:1.21.6-alpine3.18 AS builder
WORKDIR /app

RUN apk add --no-cache tzdata

COPY ../../chat .

RUN go  build -v -ldflags="-w -s" -o app ./cmd/main.go

FROM alpine:3.18
WORKDIR /app

COPY --from=builder /usr/share/zoneinfo /usr/share/zoneinfo


ENV TZ=Asia/Qyzylorda

COPY --from=builder /app .

CMD ["sh", "-c", "./app"]
