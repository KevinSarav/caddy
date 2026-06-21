ARG CADDY_VERSION=2.11
ARG DESEC_MODULE_VERSION=v1.1.0

FROM caddy:${CADDY_VERSION}-builder AS builder

ARG DESEC_MODULE_VERSION
RUN --mount=type=cache,target=/go/pkg/mod \
    --mount=type=cache,target=/root/.cache/go-build \
    xcaddy build \
    --with github.com/caddy-dns/desec@${DESEC_MODULE_VERSION}

FROM caddy:${CADDY_VERSION}

COPY --from=builder /usr/bin/caddy /usr/bin/caddy
