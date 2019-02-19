FROM golang:1.11-alpine3.9

COPY . /go/src/queen-product-ms
WORKDIR /go/src/queen-product-ms

RUN apk --no-cache --update upgrade && \
    apk add --no-cache git curl && \
    go get -u github.com/golang/dep/cmd/dep && \
    go get -u github.com/go-swagger/go-swagger/cmd/swagger && \
    swagger generate server -f swagger.yml -A queen-product-ms && \
    dep init && \
    go install /go/src/queen-product-ms/cmd/queen-product-ms-server/

ENTRYPOINT /go/bin/queen-product-ms-server --port 3000 --host 0.0.0.0

EXPOSE 3000

# CMD ["go", "run", "/go/src/queen-product-ms/cmd/queen-product-ms-server/main.go", "--port=8000"]
