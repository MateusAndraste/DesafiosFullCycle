FROM golang:1.16 AS builder

WORKDIR /opt/go/app

COPY main.go .

RUN go mod init example.com/m
RUN CGO_ENABLED=0 go build -ldflags="-s -w" -o ./rocks


FROM scratch
COPY --from=builder /opt/go/app/rocks /rocks

ENTRYPOINT [ "/rocks" ]
