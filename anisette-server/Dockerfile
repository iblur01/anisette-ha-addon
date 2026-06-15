FROM rust:alpine AS builder

RUN apk add --no-cache musl-dev git
RUN git clone --depth 1 https://github.com/Dadoum/anisette-v3-server /build
WORKDIR /build
RUN cargo build --release

FROM alpine:3.19

RUN apk add --no-cache libgcc ca-certificates

COPY --from=builder /build/target/release/anisette-v3-server /usr/local/bin/anisette-v3-server

WORKDIR /data

EXPOSE 6969

CMD ["/usr/local/bin/anisette-v3-server"]
