FROM golang:alpine AS builder

RUN export PATH=$PATH:/usr/local/go/bin

WORKDIR /

RUN mkdir /usr/app

WORKDIR /usr/app

COPY fullcycle.go .

RUN go mod init fullcycle
RUN go build -o fullcycle
RUN ./fullcycle


FROM scratch
WORKDIR /
COPY --from=builder /usr/app/ /
ENTRYPOINT ["/fullcycle"]

