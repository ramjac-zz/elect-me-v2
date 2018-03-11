FROM golang:1.9.4 as builder
# install glide
RUN go get -u github.com/golang/dep/cmd/dep
# setup the working directory
WORKDIR /go/src/app
ADD Gopkg.lock Gopkg.lock
ADD Gopkg.toml Gopkg.toml
# add source code
ADD src src
# install dependencies
RUN dep ensure
# build the source
RUN go build src/main.go
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o main src/main.go

# use a minimal alpine image
FROM alpine:latest
# add ca-certificates in case you need them
RUN apk --no-cache add ca-certificates
# set working directory
WORKDIR /root
# copy the binary from builder
COPY --from=builder /go/src/app/main .
# run the binary
CMD ["./main"]