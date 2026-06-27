# FNNet Monitor

轻量级飞牛NAS系统监控Web工具，**原生应用**，无需Docker部署。

## 功能特性

- **CPU监控**: 核心频率、温度、负载、Turbo Boost、逐核可视化
- **内存监控**: RAM/Swap使用量、缓存、实时更新
- **网络监控**: 实时网速、流量统计、60秒趋势图、网卡状态
- **磁盘监控**: 物理硬盘信息、SMART健康检测、分区使用率、I/O统计
- **进程排行**: TOP 20进程，CPU/内存占用颜色标记

## 技术栈

- 后端: Python 3 + Flask + psutil
- 前端: HTML/CSS/JS + SSE实时推送
- 运行方式: **原生应用**，直接在宿主机运行

## 飞牛安装方式

### 方式一：应用中心安装（推荐）

1. 下载最新 `.fpk` 安装包
2. 打开飞牛NAS → 应用中心 → 手动安装
3. 选择 `.fpk` 文件上传安装
4. 安装完成后在桌面点击图标即可使用

### 方式二：fnpack打包

```bash
# 安装fnpack工具
# 进入项目目录执行打包
fnpack build

# 生成的 .fpk 文件可直接在飞牛应用中心安装
```

## 原生应用目录结构

```
fnnet-monitor/
├── manifest              # 应用元信息
├── config/
│   ├── privilege         # 权限配置（root模式）
│   └── resource          # 资源类型（app）
├── cmd/
│   └── main              # 生命周期脚本
├── app/
│   ├── app.py            # Flask后端
│   ├── requirements.txt  # Python依赖
│   ├── ui/               # 桌面入口配置
│   ├── templates/        # HTML模板
│   └── static/           # CSS/JS资源
├── ICON.PNG              # 64x64 图标
├── ICON_256.PNG          # 256x256 图标
├── fnpack.json           # FnDepot元数据索引
└── README.md
```

## 端口

- 默认端口: 5000
- Web界面: http://localhost:5000

## 许可证

MIT
