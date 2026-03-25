FROM python:3.12-slim

RUN sed -i "s/deb.debian.org/mirrors.cloud.tencent.com/g" /etc/apt/sources.list.d/debian.sources && sed -i "s/security.debian.org/mirrors.cloud.tencent.com/g" /etc/apt/sources.list.d/debian.sources

RUN apt-get update && apt-get install -y --no-install-recommends \
    iputils-ping \
    wget xz-utils \
    && rm -rf /var/lib/apt/lists/*

# 安装 ffmpeg 8.0.1 静态构建
RUN wget -q https://github.com/BtbN/FFmpeg-Builds/releases/download/latest/ffmpeg-n8.0.1-linux64-gpl-8.0.tar.xz -O /tmp/ffmpeg.tar.xz && \
    tar -xf /tmp/ffmpeg.tar.xz -C /tmp && \
    cp /tmp/ffmpeg-n8.0.1-linux64-gpl-8.0/bin/* /usr/local/bin/ && \
    rm -rf /tmp/ffmpeg*

WORKDIR /app

COPY ../.. /app

RUN pip config set global.index-url https://mirrors.cloud.tencent.com/pypi/simple && \
    pip install --no-cache-dir -e .

WORKDIR /app/examples/rtsp

CMD ["python", "rtsp.py"]
