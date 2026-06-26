# FNNet Monitor

轻量级飞牛NAS系统监控Web工具，提供CPU、内存、网络、磁盘、进程实时监控。

## 功能特性

- **CPU监控**: 核心频率、温度、负载、Turbo Boost、逐核可视化
- **内存监控**: RAM/Swap使用量、缓存、实时更新
- **网络监控**: 实时网速、流量统计、60秒趋势图、网卡状态
- **磁盘监控**: 物理硬盘信息、SMART健康检测、分区使用率、I/O统计
- **进程排行**: TOP 20进程，CPU/内存占用颜色标记
- **网口管理**: 扫描网口、查看状态、配置IP/子网/网关/DNS

## 技术栈

- 后端: Flask (Python) + psutil
- 前端: 纯 HTML/CSS/JS + SSE实时推送
- 部署: Docker（privileged模式）

## 安装

使用Docker Compose一键部署：

```bash
docker compose up -d
```

访问 http://localhost:5990 即可使用。

## 配置

端口默认为5990，可通过docker-compose.yml修改。

## 许可证

MIT
