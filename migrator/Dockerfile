FROM golang:1.21.6-alpine3.18 AS builder
WORKDIR /src
COPY . .
RUN go  build -v -ldflags="-w -s" -o server ./cmd/main.go

FROM golang:1.21.6-alpine3.18
WORKDIR /app

RUN apk add --no-cache tzdata && \ ENV TZ=Asia/Almaty

COPY --from=builder /src/server .
COPY --from=builder /src/config/local.yaml .

CMD ["sh", "-c", "./main"]
