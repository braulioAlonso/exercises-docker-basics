FROM golang:1.27

WORKDIR /usr/src/app

COPY . .

RUN git config --global http.sslVerify false

ENV GOPROXY=direct

ENV GOSUMDB=off

RUN go build

ENV PORT=8080

EXPOSE 8080

CMD ["./server"]
