FROM python:3.12-slim

RUN sed -i "s/deb.debian.org/mirrors.cloud.tencent.com/g" /etc/apt/sources.list.d/debian.sources && sed -i "s/security.debian.org/mirrors.cloud.tencent.com/g" /etc/apt/sources.list.d/debian.sources

RUN apt-get update && apt-get install -y --no-install-recommends \
    libgl1 \
    libglib2.0-0 \
    iputils-ping \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

COPY ../.. /app

RUN pip config set global.index-url https://mirrors.cloud.tencent.com/pypi/simple && \
    pip install --no-cache-dir -e . opencv-python-headless

WORKDIR /app/examples/web

EXPOSE 8080

CMD ["python", "web.py"]
