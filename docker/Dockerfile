# Base image 설정
FROM debian:bullseye-slim

# 필요한 패키지 설치
RUN apt-get update && \
    apt-get install -y curl tar && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /workspace/RedisShake
ENV PATH="/workspace/RedisShake:${PATH}"

# tarball 다운로드 및 압축 해제
RUN curl -LO https://github.com/tair-opensource/RedisShake/releases/download/v3.1.11/redis-shake-linux-amd64.tar.gz && \
    tar -xzf redis-shake-linux-amd64.tar.gz && \
    rm redis-shake-linux-amd64.tar.gz

# Make redis-shake globally accessible
RUN chmod +x redis-shake && \
    mv redis-shake /usr/bin/ && \
    chmod +x sync.toml scan.toml restore.toml

USER 1001