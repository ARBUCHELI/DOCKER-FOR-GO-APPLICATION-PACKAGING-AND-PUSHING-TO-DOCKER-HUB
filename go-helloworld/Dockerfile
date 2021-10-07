FROM golang:alpine
LABEL maintainer="Andres R. Bucheli"

WORKDIR /go/src/app

ADD . .

RUN go  mod init

RUN go build  -o helloworld

EXPOSE 6111

CMD ["./helloworld"]