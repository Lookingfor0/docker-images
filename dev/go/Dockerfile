FROM kubernetes/pause:go AS pause

FROM golang:1.15-buster
COPY --from=pause /pause /pause
# GOPATH: /go
ENV GO111MODULE=on
ENV GOPROXY="https://goproxy.cn"
ENV HTTP_PROXY=http://host.docker.internal:7890
ENV HTTPS_PROXY=http://host.docker.internal:7890
ENV NO_PROXY=localhost,host.docker.internal,127.0.0.1,192.168.0.0/16,172.0.0.0.8
RUN echo 'Acquire::http::Proxy "http://host.docker.internal:7890";\nAcquire::https::Proxy "http://host.docker.internal:7890";' >> /etc/apt/apt.conf.d/80proxy.conf && \
    apt-get update && apt-get -y install build-essential && \
    go get github.com/go-delve/delve/cmd/dlv

# use pause instead
# CMD ["tail", "-f", "/dev/null"]
# CMD ["dlv", "debug", "--listen", ":23456", "--build-flags=''", "."]
CMD ["/pause"]

