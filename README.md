<p align="center">
  <img src="./img/MusicSync.png" width="112" alt="MusicSync Logo">
</p>

<h1 align="center">MusicSync</h1>

<p align="center">
  自托管、多用户、支持 LX Music 同步与 OpenSubsonic 的 Web 音乐聚合服务
</p>

<p align="center">
  <a href="https://github.com/lincolnpark2000/MusicSync/releases"><img src="https://img.shields.io/github/v/release/lincolnpark2000/MusicSync?label=Release" alt="Release"></a>
  <a href="https://hub.docker.com/r/lincolnpark2000/musicsync"><img src="https://img.shields.io/docker/pulls/lincolnpark2000/musicsync?label=Docker%20Pulls" alt="Docker Pulls"></a>
  <a href="./LICENSE"><img src="https://img.shields.io/badge/license-MIT-green" alt="License"></a>
</p>

MusicSync 是一个以 Docker 部署为主的自托管音乐服务。它既可以作为浏览器中的独立音乐播放器，也可以作为 LX Music 客户端的数据同步服务，并为兼容 Subsonic / OpenSubsonic 的客户端提供音乐库访问能力。

项目本身不内置、不提供任何音乐播放源。播放地址需要由用户自行配置兼容 LX Music 协议的第三方自定义源。

## 主要特性

### 音乐搜索与浏览

- 支持酷我、酷狗、QQ 音乐、网易云、咪咕、Bilibili、YouTube Music 等平台搜索。
- 支持多平台聚合搜索、热搜、搜索历史和多源自动切换。
- 支持排行榜、分类歌单、YouTube Music 官方心情 / 活动 / 流派歌单。
- 支持歌手详情、专辑详情、相关歌曲和高清封面。
- 支持收藏歌曲、歌单、歌手、专辑，并创建和管理自己的歌单。

### 播放器与歌词

- 支持多种播放器样式、播放队列、循环 / 随机播放和歌词同步滚动。
- 支持歌词卡片分享、封面展示和歌曲详情补全。
- 支持系统 Media Session / SMTC 媒体控制，并可在系统媒体控制栏显示当前歌词。
- 支持锁屏或切换后台时暂停播放，回到前台后自动恢复。
- 支持按播放时长或播放歌曲数设置睡眠定时关闭。
- 支持深色模式、浅色模式、响应式移动端页面和 PWA 安装。

### 下载与缓存

- 支持浏览器下载和服务器落盘下载。
- 支持单曲、批量下载以及下载前确认下载方式、音质和歌词文件。
- 支持 `128k`、`320k`、`FLAC`、`FLAC24BIT` 等音质选择与质量替换策略。
- 支持下载队列、实时进度、速度、状态管理和完成记录。
- 支持为下载文件嵌入歌曲元数据与封面，并校验异常文件和版权提示音。
- 支持浏览器缓存与服务器缓存，提供缓存索引、命名模板、容量限制和自动清理。
- YouTube Music 音频可通过后端集成的 `yt-dlp` 解析和下载。

### 订阅与自动化

- 支持订阅歌手、专辑和歌单。
- 支持定时检查、手动检查、后台异步扫描和发现新歌后自动下载。
- 支持扫描并发、下载并发、新增歌曲策略和音质升级策略。
- 支持查看订阅运行状态、扫描进度、歌曲列表和下载结果。

### 多用户、权限与同步

- 支持多用户登录，每位用户拥有独立的收藏、歌单、历史、下载、订阅和设置。
- 支持用户组和细粒度权限，包括播放、历史、歌单、同步、自定义源、下载、缓存、设置和服务器管理。
- 支持 LX Music 客户端歌单同步。
- 支持 Subsonic / OpenSubsonic 常用接口，可连接音流、Symfonium 等兼容客户端。
- 支持播放历史、歌单、收藏、歌手、专辑、封面、歌词、搜索和串流等 Subsonic 能力。

### 数据安全与通知

- 支持用户数据导入、导出和用户级 WebDAV 同步。
- 支持管理员全局 WebDAV 备份、恢复、远程备份列表和定时自动备份。
- 支持用户快照，恢复快照前会自动创建保护性备份。
- 支持 Telegram Bot 搜索、下载、订阅和手动触发订阅检查。
- 支持 Telegram、Server 酱和 PushPlus 通知。
- 支持登录提醒、订阅进度、新歌发现和下载完成等事件通知。

### 部署与更新

- 支持 Docker / Docker Compose 部署。
- 提供 AMD64 与 ARM64 镜像发布脚本和独立 ARM64 标签。
- 支持自定义数据、下载和缓存目录，适合挂载到 SSD 或 NAS。
- 支持 HTTP / HTTPS 代理、用户自定义源代理和域名分流。
- 页面启动时自动检查 GitHub Release；支持稍后提醒、立即查看和忽略当前 Release。

## 页面预览

<table>
  <tr>
    <td align="center"><b>搜索首页</b></td>
    <td align="center"><b>Bilibili 搜索</b></td>
    <td align="center"><b>YouTube Music</b></td>
    <td align="center"><b>排行榜</b></td>
  </tr>
  <tr>
    <td><img src="./img/搜索页面A.PNG" width="190"></td>
    <td><img src="./img/哔哩哔哩搜索.png" width="190"></td>
    <td><img src="./img/youtube搜索.png" width="190"></td>
    <td><img src="./img/榜单页面.PNG" width="190"></td>
  </tr>
  <tr>
    <td align="center"><b>歌单浏览</b></td>
    <td align="center"><b>播放器</b></td>
    <td align="center"><b>歌词页面</b></td>
    <td align="center"><b>缓存中心</b></td>
  </tr>
  <tr>
    <td><img src="./img/歌单页面.PNG" width="190"></td>
    <td><img src="./img/播放器.PNG" width="190"></td>
    <td><img src="./img/播放器歌词.PNG" width="190"></td>
    <td><img src="./img/缓存中心.PNG" width="190"></td>
  </tr>
  <tr>
    <td align="center"><b>Telegram 搜索下载</b></td>
    <td align="center"><b>Telegram 添加订阅</b></td>
    <td align="center"><b>多用户与服务器同步</b></td>
    <td align="center"><b>深色模式</b></td>
  </tr>
  <tr>
    <td><img src="./img/tg命令搜索下载.png" width="190"></td>
    <td><img src="./img/tg命令添加订阅.png" width="190"></td>
    <td><img src="./img/多用户管理+服务器同步.png" width="190"></td>
    <td><img src="./img/微信图片_20260403214343_24_11.png" width="190"></td>
  </tr>
</table>

## Docker 快速部署

### Docker Compose

创建 `docker-compose.yml`：

```yaml
services:
  musicsync:
    image: lincolnpark2000/musicsync:latest
    container_name: musicsync
    restart: unless-stopped
    ports:
      - "5566:5566"
    environment:
      - PORT=5566
      - NODE_ENV=production
      - DATA_DIR=/app/data
      - DOWNLOAD_DIR=/app/downloads
      - CACHE_DIR=/app/cache
      - JWT_SECRET=请替换为随机长字符串
      - JSON_BODY_LIMIT=8mb
    volumes:
      - ./data:/app/data
      - ./downloads:/app/downloads
      - ./cache:/app/cache
```

启动服务：

```bash
docker compose up -d
```

浏览器访问：

```text
http://服务器IP:5566
```

首次启动会创建默认管理员：

```text
用户名：admin
密码：admin
```

登录后请立即修改默认密码。

### ARM64 部署

ARM64 设备可使用独立标签：

```yaml
image: lincolnpark2000/musicsync:latest-arm64
```

版本标签格式为：

```text
lincolnpark2000/musicsync:v版本号-arm64
```

## 首次使用

1. 使用默认管理员登录并修改密码。
2. 打开“设置中心 → 扩展设置”，导入兼容 LX Music 协议的自定义源。
3. 按需要配置默认音质、缓存策略、下载目录和订阅行为。
4. 需要远程通知时，配置 Telegram 或微信推送。
5. 需要多端同步时，配置 LX Music、WebDAV 或 Subsonic 客户端。

## LX Music 客户端同步

MusicSync 可以作为 LX Music 客户端的同步服务端。

| 配置项 | 内容 |
|---|---|
| 同步地址 | `http://服务器IP:5566/用户名` |
| 同步密码 | 当前用户的登录密码 |

如果旧用户无法同步，请在网页中重新修改一次密码，使服务端生成最新同步凭据。

## Subsonic / OpenSubsonic

兼容客户端可使用以下配置：

| 配置项 | 内容 |
|---|---|
| 服务地址 | `http://服务器IP:5566` |
| 用户名 | MusicSync 用户名 |
| 密码 | MusicSync 用户密码 |

服务端入口为 `/rest/*`，支持常用歌单、收藏、歌手、专辑、歌词、封面、搜索、播放记录与音频串流接口。

## Telegram Bot

在“设置中心 → 通知管理”中配置 Bot Token 和 Chat ID 后，可以接收通知并使用机器人操作 MusicSync。

常用命令示例：

```text
/start
/help
/search 周杰伦 稻香
/download 周杰伦 稻香
/sub 歌手 Taylor Swift
/sub_list
/sub_check
```

## 常用环境变量

| 环境变量 | 默认值 | 说明 |
|---|---:|---|
| `PORT` | `5566` | 服务监听端口 |
| `DATA_DIR` | `/app/data` | 用户、配置、快照等数据目录 |
| `DOWNLOAD_DIR` | `/app/downloads` | 服务器下载目录 |
| `CACHE_DIR` | `/app/cache` | 服务器音频缓存目录 |
| `JWT_SECRET` | 内置默认值 | JWT 密钥，公网部署必须修改 |
| `JSON_BODY_LIMIT` | `8mb` | JSON 请求体大小限制 |
| `USER_API_AUTO_REFRESH` | `1` | 是否定时刷新自定义源 |
| `USER_API_AUTO_REFRESH_ON_BOOT` | `1` | 启动时是否刷新自定义源 |
| `USER_API_AUTO_REFRESH_INTERVAL_MINUTES` | `180` | 自定义源刷新间隔 |
| `USER_API_PROXY` | 空 | 自定义源、YouTube 等服务使用的代理 |
| `USER_API_PROXY_MODE` | `china_whitelist` | 代理分流模式 |
| `USER_API_PROXY_DOMAINS` | 空 | 额外需要代理的域名 |
| `HTTP_PROXY` / `HTTPS_PROXY` | 空 | 进程级 HTTP / HTTPS 代理 |
| `NO_PROXY` | 空 | 代理绕过列表 |
| `UPDATE_CHECK_REPOSITORY` | `lincolnpark2000/MusicSync` | 自动更新检查使用的 GitHub 仓库 |
| `UPDATE_CHECK_CACHE_TTL_MS` | `900000` | Release 检查缓存时间 |
| `GITHUB_TOKEN` | 空 | 可选，用于提高 GitHub API 限额 |

## 数据目录

建议将数据、下载和缓存目录分别持久化：

```yaml
volumes:
  - /your/path/musicsync/data:/app/data
  - /your/path/musicsync/downloads:/app/downloads
  - /your/path/musicsync/cache:/app/cache
```

升级容器不会影响已挂载的数据。执行重要升级或迁移前，建议先在管理后台创建快照或执行 WebDAV 全局备份。

## 自定义源与版权说明

- MusicSync 不提供、不内置、不分发任何受版权保护的音乐内容或播放源。
- 自定义源、代理和相关内容由用户自行配置，使用者应自行判断其合法性与合规性。
- 请遵守所在地法律法规并支持正版音乐。
- 本项目仅用于学习、研究和个人技术实践。

## 相关链接

- GitHub Releases：<https://github.com/lincolnpark2000/MusicSync/releases>
- Docker Hub：<https://hub.docker.com/r/lincolnpark2000/musicsync>

## License

[MIT](./LICENSE)
