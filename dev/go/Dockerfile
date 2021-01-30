FROM golang:1.15-alpine

RUN go env -w GO111MODULE=on && go env -w GOPROXY=https://goproxy.cn,direct && go get github.com/go-delve/delve/cmd/dlv
# GOPATH: /go

CMD ["tail", "-f", "/dev/null"]
