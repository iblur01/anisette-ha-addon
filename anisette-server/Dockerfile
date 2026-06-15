FROM debian:stable-20250520-slim AS builder

RUN apt-get update && apt-get install --no-install-recommends -y \
    ca-certificates ldc git clang dub libz-dev libssl-dev libplist-dev libplist-2.0-4 \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

RUN git clone --depth 1 https://github.com/Dadoum/anisette-v3-server /opt/anisette-v3-server

WORKDIR /opt/anisette-v3-server

RUN DC=ldc2 dub build -c "static" --build-mode allAtOnce -b release --compiler=ldc2

FROM debian:stable-slim

RUN apt-get update && apt-get install --no-install-recommends -y \
    ca-certificates curl libplist-dev libplist-2.0-4 \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

WORKDIR /data

COPY --from=builder /opt/anisette-v3-server/anisette-v3-server /usr/local/bin/anisette-v3-server

RUN mkdir -p /data/provisioning

EXPOSE 6969

CMD ["/usr/local/bin/anisette-v3-server"]
