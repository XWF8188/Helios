# Helios

<div align="center">
  <img src="logo.png" alt="Helios Logo" width="120">
</div>

> 🎬 **Helios** 是 [Selene](https://github.com/XWF8188/Selene) 所需 API 的 golang 实现。设计目标是单容器、单用户、最小化。

<div align="center">

![Go](https://img.shields.io/badge/Go-1.23.7-00ADD8?logo=go)
![Docker](https://img.shields.io/badge/Docker-支持-2496ED?logo=docker)
![SQLite](https://img.shields.io/badge/SQLite-数据库-003B57?logo=sqlite)

</div>

### 请不要在 B站、小红书、微信公众号、抖音、今日头条或其他中国大陆社交平台发布视频或文章宣传本项目，不授权任何"科技周刊/月刊"类项目或站点收录本项目。

## 📋 功能特性

- 🎬 **多源搜索** - 支持多个影视资源站点的搜索
- 🔍 **实时搜索** - 提供SSE实时搜索功能
- ❤️ **收藏管理** - 收藏喜欢的影视作品
- 📚 **搜索历史** - 记录和管理搜索历史
- 🎯 **播放记录** - 追踪播放进度和记录
- 🔐 **用户认证** - 基于用户名密码的安全认证
- ⚡ **高性能** - 使用Go语言开发，性能优异
- 🗄️ **数据持久化** - SQLite数据库存储用户数据
- 🐳 **容器化** - 支持Docker部署

## 🚀 快速开始

### 环境要求

- Go 1.23.7+
- Docker (可选)

### 环境变量配置

在运行前需要设置以下环境变量：

```bash
export USERNAME="your_username"           # 用户名
export PASSWORD="your_password"           # 密码
export SUBSCRIPTION_URL="https://your_subscription_url.com"  # 订阅配置URL
```

订阅 URL 请参考[这里](https://github.com/XWF8188/LunaTV?tab=readme-ov-file#%E2%9A%99%EF%B8%8F%20%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6)

### 本地运行

1. 克隆项目
```bash
git clone https://github.com/XWF8188/Helios.git
cd Helios
```

2. 设置环境变量
```bash
export USERNAME="your_username"
export PASSWORD="your_password" 
export SUBSCRIPTION_URL="https://your_subscription_url.com"
```

3. 安装依赖并运行
```bash
go mod download
go run .
```

服务器将在 `http://localhost:8080` 启动。

### Docker 部署

#### 方式一：使用 Docker Compose（推荐）

1. 创建 `docker-compose.yml` 文件：
```yaml
version: '3.8'

services:
  helios:
    image: ghcr.io/XWF8188/helios:latest
    ports:
      - "8080:8080"
    environment:
      - USERNAME=${USERNAME:-your_username}
      - PASSWORD=${PASSWORD:-your_password}
      - SUBSCRIPTION_URL=${SUBSCRIPTION_URL:-https://your_subscription_url.com}
    volumes:
      # 持久化数据库文件
      - ./data:/data
    restart: unless-stopped
```

2. 启动服务：
```bash
docker compose up -d
```

#### 方式二：直接使用 Docker 命令

1. 创建数据目录：
```bash
mkdir -p ./data
```

2. 启动容器：
```bash
docker run -d \
  --name helios \
  -p 8080:8080 \
  -e USERNAME="your_username" \
  -e PASSWORD="your_password" \
  -e SUBSCRIPTION_URL="https://your_subscription_url.com" \
  -v ./data:/data \
  --restart unless-stopped \
  ghcr.io/XWF8188/helios:latest
```

## ⚠️ 免责声明

本项目仅供学习和研究使用，请遵守相关法律法规。
