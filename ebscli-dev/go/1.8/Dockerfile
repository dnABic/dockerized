FROM buildpack-deps:wheezy-scm

# gcc for cgo
RUN apt-get update && apt-get install -y --no-install-recommends \
      build-essential \
      g++ \
      gcc \
      git-core \
      libc6-dev \
      make \
      man \
      pkg-config \
      unzip \
      util-linux \
      zip \
  && rm -rf /var/lib/apt/lists/*

ENV GOLANG_VERSION 1.8rc3
ENV GOLANG_DOWNLOAD_URL https://golang.org/dl/go$GOLANG_VERSION.linux-amd64.tar.gz
ENV GOLANG_DOWNLOAD_SHA256 0ff3faba02ac83920a65b453785771e75f128fbf9ba4ad1d5e72c044103f9c7a

RUN curl -fsSL "$GOLANG_DOWNLOAD_URL" -o golang.tar.gz \
  && echo "$GOLANG_DOWNLOAD_SHA256  golang.tar.gz" | sha256sum -c - \
  && tar -C /usr/local -xzf golang.tar.gz \
  && rm golang.tar.gz

ENV GOPATH /go
ENV PATH $GOPATH/bin:/usr/local/go/bin:$PATH

RUN mkdir -p "$GOPATH/src" "$GOPATH/bin" && chmod -R 777 "$GOPATH"
WORKDIR $GOPATH

#COPY go-wrapper /usr/local/bin/
