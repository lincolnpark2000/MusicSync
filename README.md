# MusicSync

一个基于 Docker 部署的 Web 音乐播放器，**本身不内置任何音乐源**，通过接入第三方自定义音源来实现音乐播放。完全兼容**洛雪音乐（LX Music）**自定义源协议，支持多源聚合、自动切换与本地缓存。

---

## 功能特点

- **无内置源**：本项目不提供任何音乐版权内容，所有播放能力来自用户自行配置的第三方自定义源
- **兼容洛雪源**：完整支持 LX Music 自定义源协议，可直接导入社区现有的源
- **多源聚合 & 自动切换**：同时配置多个源后，播放失败时自动切换到下一个可用源，无缝寻找最优线路
- **本地缓存**：播放过的歌曲自动缓存到本地，再次播放直接读取缓存，省流量、响应更快
- **多平台搜索**：支持酷我、酷狗、QQ 音乐、网易云、咪咕等平台聚合搜索
- **排行榜 & 歌单**：浏览各平台排行榜及精选歌单，支持按专区分类筛选
- **高音质**：支持 FLAC / FLAC24BIT / 320K 等多种音质显示与筛选
- **歌词同步**：播放界面实时滚动歌词显示
- **Docker 一键部署**：无需复杂环境，Docker Compose 即可运行

---

## 截图预览

<table>
  <tr>
    <td align="center"><b>搜索页面</b></td>
    <td align="center"><b>平台选择</b></td>
    <td align="center"><b>歌曲列表</b></td>
    <td align="center"><b>歌词页面</b></td>
  </tr>
  <tr>
    <td><img src="./img/搜索页面A.PNG" width="180"/></td>
    <td><img src="./img/搜索页面B.PNG" width="180"/></td>
    <td><img src="./img/播放器.PNG" width="180"/></td>
    <td><img src="./img/播放器歌词.PNG" width="180"/></td>
  </tr>
  <tr>
    <td align="center"><b>排行榜</b></td>
    <td align="center"><b>歌单分类</b></td>
    <td align="center"><b>缓存中心</b></td>
    <td></td>
  </tr>
  <tr>
    <td><img src="./img/榜单页面.PNG" width="180"/></td>
    <td><img src="./img/歌单页面.PNG" width="180"/></td>
    <td><img src="./img/缓存中心.PNG" width="180"/></td>
    <td></td>
  </tr>
</table>

---

## 快速开始（Docker 部署）

### 前置条件

- 已安装 [Docker](https://docs.docker.com/get-docker/) 和 [Docker Compose](https://docs.docker.com/compose/install/)
- 自行准备兼容洛雪协议的第三方自定义音源地址

### 1. 下载配置文件

```bash
# 下载 docker-compose 配置
curl -O https://raw.githubusercontent.com/your-username/musicsync/main/docker-compose.example.yml

# 重命名为正式配置
mv docker-compose.example.yml docker-compose.yml
```

或者直接复制以下内容保存为 `docker-compose.yml`：

```yaml
version: "3.8"
services:
  musicsync:
    image: lincolnpark2000/musicsync:latest
    container_name: musicsync
    restart: unless-stopped
    ports:
      # 左侧改为你想要的端口号
      - "5566:5566"
    environment:
      - PORT=5566
      - NODE_ENV=production
      - DATA_DIR=/app/data
      - DOWNLOAD_DIR=/app/downloads
      # 可选：为自定义音源单独设置出口代理
      # - USER_API_PROXY=http://your-proxy:port
      # 可选：通用代理（仅在必要时设置）
      # - HTTP_PROXY=http://your-proxy:port
      # - HTTPS_PROXY=http://your-proxy:port
      # - NO_PROXY=127.0.0.1,localhost,musicsync
    volumes:
      - musicsync_data:/app/data
      - musicsync_downloads:/app/downloads

volumes:
  musicsync_data:
  musicsync_downloads:
```

### 2. 启动服务

```bash
docker compose up -d
```

### 3. 访问

打开浏览器访问 `http://localhost:5566`（或你配置的端口）。

---

## 配置自定义音源

> MusicSync 本身**不能播放任何音乐**，必须先配置自定义音源。

### 添加方式

1. 打开 MusicSync 网页界面
2. 进入 **设置 → 自定义音源**
3. 填入兼容洛雪协议的音源 URL，保存即可

### 多源自动切换

支持同时添加多个音源地址。当某个源获取失败时，系统会自动尝试下一个源，无需手动干预。

### 推荐音源格式

兼容 [洛雪音乐自定义源](https://github.com/pdone/lx-music-source) 协议，社区现有的 LX Music 源可直接使用。

---

## 环境变量说明

| 变量名 | 默认值 | 说明 |
|--------|--------|------|
| `PORT` | `5566` | 服务监听端口 |
| `DATA_DIR` | `/app/data` | 数据存储目录（用户数据、配置等） |
| `DOWNLOAD_DIR` | `/app/downloads` | 缓存文件存储目录 |
| `USER_API_AUTO_REFRESH` | `1` | 是否自动刷新自定义源（1=开启，0=关闭） |
| `USER_API_AUTO_REFRESH_INTERVAL_MINUTES` | `180` | 自动刷新间隔（分钟） |
| `USER_API_PROXY` | 空 | 为自定义音源单独设置的出口代理 |
| `HTTP_PROXY` / `HTTPS_PROXY` | 空 | 全局出口代理（仅需要代理时设置） |

---

## 数据持久化

默认使用 Docker 具名卷存储数据。如需挂载到宿主机指定目录，将 `volumes` 改为绝对路径：

```yaml
volumes:
  - /your/path/data:/app/data
  - /your/path/downloads:/app/downloads
```

---

## 注意事项

- 本项目**不提供、不内置、不分发**任何受版权保护的音乐内容
- 自定义音源由用户自行配置，相关内容的合规性由用户自负
- 本项目仅用于学习与技术研究目的

---

## License

[MIT](./LICENSE)
