FROM snowdreamtech/go:1.23.3-bookworm AS builder

ENV FRP_VERSION=0.61.1

RUN mkdir /workspace

WORKDIR /workspace

COPY src/resource.go .

RUN set -eux \
    && apt-get -qqy update  \
    && apt-get -qqy install --no-install-recommends \ 
    make \
    && wget -c https://github.com/fatedier/frp/archive/refs/tags/v${FRP_VERSION}.tar.gz \
    && tar zxvf v${FRP_VERSION}.tar.gz \
    && cd frp-${FRP_VERSION} \
    && mv ../resource.go ./pkg/util/vhost/resource.go \
    && make \
    && cp -rfv bin conf /workspace/ \
    && apt-get -qqy --purge autoremove \
    && apt-get -qqy clean \
    && rm -rf /var/lib/apt/lists/* \
    && rm -rf /tmp/* \
    && rm -rf /var/tmp/*


FROM snowdreamtech/debian:12.8.0

# OCI annotations to image
LABEL org.opencontainers.image.authors="HEDW" \
    org.opencontainers.image.title="Frps Image Based On Alpine" \
    org.opencontainers.image.description="Docker Images for Frps On Debian. (i386,amd64,arm32v5,arm32v7,arm64,mips64le,ppc64le,s390x)" \
    org.opencontainers.image.documentation="https://hub.docker.com/r/hedw/frps" \
    org.opencontainers.image.base.name="hedw/frps:alpine" \
    org.opencontainers.image.licenses="MIT" \
    org.opencontainers.image.source="https://github.com/yesgit/frp-404" \
    org.opencontainers.image.vendor="HEDW" \
    org.opencontainers.image.version="0.61.1" \
    org.opencontainers.image.url="https://github.com/yesgit/frp-404"

COPY --from=builder /workspace/bin/frps /usr/bin/
COPY --from=builder /workspace/conf/frps.toml /etc/frp/

ENTRYPOINT ["/usr/bin/frps"]

CMD ["-c", "/etc/frp/frps.toml"]