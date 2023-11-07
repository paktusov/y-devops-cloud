# Stage 1: Build the application
FROM golang:1.21 AS build

WORKDIR /usr/src/app
COPY . .
WORKDIR ./catgpt

RUN go mod download
RUN CGO_ENABLED=0 go build -o /go/bin/app

# Stage 2: Create the final container
FROM gcr.io/distroless/static-debian12:latest-amd64

COPY --from=build /go/bin/app /app

CMD ["/app"]