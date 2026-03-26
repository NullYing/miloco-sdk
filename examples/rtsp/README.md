# RTSP 推流示例使用说明

## 方式一：Docker 一键部署（推荐）

1. 进入目录：

```bash
cd examples/rtsp
```

2. 启动服务：

```bash
docker compose up -d
```

3. 进入推流容器交互界面（仅在有多台摄像头时需要选择设备）：

```bash
docker attach rtsp-rtsp-pusher-1
```

4. 在浏览器打开以下地址观看画面：

`http://127.0.0.1:1984/stream.html?src=live`

## 方式二：手动部署

1. 先启动 go2rtc：
   - 下载地址：<https://github.com/AlexxIT/go2rtc/releases>
   - 运行命令：

```bash
go2rtc -config go2rtc.yaml
```

2. 运行 RTSP 推流脚本：

```bash
uv run python examples/rtsp/rtsp.py
```

```bash
uv run python examples/rtsp/rtsp.py --audio
```

- `python examples/rtsp/rtsp.py`：仅视频
- `python examples/rtsp/rtsp.py --audio`：视频 + 音频

3. 在浏览器打开以下地址观看画面：

`http://127.0.0.1:1984/stream.html?src=live`
