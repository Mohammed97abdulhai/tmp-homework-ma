# syntax=docker/dockerfile:1

#start building stage
FROM golang:alpine as builder

RUN apk update && apk add --no-cache git

WORKDIR /app

COPY go-app/go.mod ./

COPY go-app/go.sum ./

RUN go mod download 

COPY go-app/main.go ./

COPY go-app/internal ./internal

COPY go-app/.env  ./

RUN go build -o ./todo-app

# Start deployment stage
FROM alpine:latest

WORKDIR /root/

COPY --from=builder /app/todo-app .
COPY --from=builder /app/.env .

Expose 8080

CMD ["./todo-app"]