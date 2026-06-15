ARG BUILD_FROM
FROM rust:alpine AS builder

RUN apk add --no-cache musl-dev git
RUN git clone --depth 1 https://github.com/Dadoum/anisette-v3-server /build
WORKDIR /build
RUN cargo build --release

FROM $BUILD_FROM

COPY --from=builder /build/target/release/anisette-v3-server /usr/local/bin/anisette-v3-server

WORKDIR /data

COPY run.sh /run.sh
RUN chmod +x /run.sh

CMD ["/run.sh"]
