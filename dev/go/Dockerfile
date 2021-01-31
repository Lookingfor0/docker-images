FROM kubernetes/pause:go AS pause

FROM golang:1.15-buster
COPY --from=pause /pause /pause
# GOPATH: /go
ENV GO111MODULE=on
ENV GOPROXY="https://goproxy.cn"
RUN apt-get update && apt-get -y install build-essential && \
    go get github.com/go-delve/delve/cmd/dlv

# use pause instead
# CMD ["tail", "-f", "/dev/null"]
# CMD ["dlv", "debug", "--listen", ":23456", "--build-flags=''", "."]
CMD ["/pause"]

