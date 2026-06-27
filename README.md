# FNNet Monitor

轻量级 NAS 系统监控 Web 工具，一条 Docker 命令即可拥有专业级可视化监控面板。

## ✨ 功能特性

- ⚡ **CPU 监控** — 使用率、核心频率、温度、负载、Turbo Boost 状态、逐核可视化
- 🧠 **内存监控** — RAM / Swap 使用量、缓存、实时更新
- 🌐 **网络监控** — 实时上传/下载速度、流量统计、60 秒趋势图、各网卡状态
- 💾 **磁盘监控** — 物理硬盘信息、SMART 健康检测、分区使用率、I/O 统计
- 🔝 **进程排行** — TOP 20 进程，CPU/内存占用颜色标记，异常进程一目了然
- 📡 **SSE 实时推送** — 无需刷新，数据每 2 秒自动更新

## 📦 快速安装

### Docker 运行

```bash
docker run -d --name fnnet-monitor -p 5000:5000 --privileged \
  --pid=host -v /sys:/sys:ro \
  ghcr.io/x1027966382/fnnet-monitor:latest
```

### Docker Compose

```bash
git clone https://github.com/x1027966382/fnnet-monitor.git
cd fnnet-monitor
docker compose up -d
```

启动后浏览器访问 `http://<你的NAS-IP>:5000` 即可打开监控面板。

## ⚠️ 注意事项

- 容器需要 **privileged** 权限和 **pid: host** 才能读取宿主机数据
- 不要挂载 `/proc`，在 fnOS 6.18 内核上会触发 apparmor 冲突
- 推荐通过 [FnDepot](https://github.com/x1027966382/FnDepot) 应用商店安装 FPK 版本

## 🛠️ 技术栈

| 组件 | 技术 |
|------|------|
| 后端 | Flask (Python) |
| 数据采集 | psutil、smartctl、/proc 文件系统 |
| 前端 | 纯 HTML / CSS / JavaScript |
| 实时通信 | Server-Sent Events (SSE) |
| 部署 | Docker |

## 📂 项目结构

```
fnnet-monitor/
├── app.py                  # Flask 后端
├── requirements.txt        # Python 依赖
├── Dockerfile              # Docker 镜像构建
├── docker-compose.yml      # Docker Compose 配置
├── templates/
│   └── index.html          # 监控面板页面
└── static/
    ├── css/style.css       # 暗色主题样式
    └── js/app.js           # 前端实时渲染逻辑
```

## 📝 API 接口

| 路径 | 说明 |
|------|------|
| `GET /` | 监控面板页面 |
| `GET /api/data` | 一次性返回全部监控数据（JSON） |
| `GET /api/stream` | SSE 实时数据流（每 2 秒推送） |
| `GET /api/cpu` | CPU 信息 |
| `GET /api/memory` | 内存信息 |
| `GET /api/network` | 网络信息 |
| `GET /api/disk` | 磁盘信息 |
| `GET /api/processes` | 进程列表 |

## 📄 License

MIT
