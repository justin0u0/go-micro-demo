FROM golang:1.14 AS builder
WORKDIR /app
ENV GO111MODULE=on
COPY . .
RUN go mod download
RUN CGO_ENABLED=0 GOOS=linux go build -a -o greeter-api

FROM alpine:latest
RUN apk --no-cache add ca-certificates
WORKDIR /app
COPY --from=builder /app/greeter-api .
ENV PARAMS=""
CMD ./greeter-api $PARAMS
