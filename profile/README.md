<div align="center">

<img src="https://raw.githubusercontent.com/OpenWrt-MTUN-XD/.github/main/profile/banner.jpg" width="880" alt="墨枢云境 · MTUN-XD">

<br><br>

### 墨枢云境 · MTUN-XD

**OpenWrt / iStoreOS 上的 Mihomo 管理套件** —— 核心、面板、配置工具与 80 端口接入，装一次全都齐。

[![最新版本](https://img.shields.io/github/v/release/OpenWrt-MTUN-XD/OpenWrt-MTUN-XD?style=flat-square&label=%E6%9C%80%E6%96%B0%E7%89%88%E6%9C%AC&color=2ea043)](https://github.com/OpenWrt-MTUN-XD/OpenWrt-MTUN-XD/releases/latest)
[![下载量](https://img.shields.io/github/downloads/OpenWrt-MTUN-XD/OpenWrt-MTUN-XD/total?style=flat-square&label=%E4%B8%8B%E8%BD%BD%E9%87%8F&color=0969da)](https://github.com/OpenWrt-MTUN-XD/OpenWrt-MTUN-XD/releases)
[![许可证](https://img.shields.io/badge/%E8%AE%B8%E5%8F%AF%E8%AF%81-MIT-3da639?style=flat-square)](https://github.com/OpenWrt-MTUN-XD/OpenWrt-MTUN-XD/blob/main/LICENSE)
[![平台](https://img.shields.io/badge/%E5%B9%B3%E5%8F%B0-OpenWrt%20%7C%20iStoreOS-ff8c00?style=flat-square)](https://github.com/OpenWrt-MTUN-XD/OpenWrt-MTUN-XD)

</div>

---

## 它是什么

把 Mihomo 的日常维护压进 LuCI 的一个菜单项：**装核心、换面板、生成配置、挂 80 端口**，不用记一堆命令，也不用为了升级面板去翻文档。

套件本体只有几十 KB，核心与面板在安装时从官方 Release 现拉，并校验 SHA-256。

## 能做什么

| | 能力 | 说明 |
| --- | --- | --- |
| 🧠 | **核心管理** | 按 CPU 架构自动选包，升级失败自动回滚 |
| 🎛️ | **面板接入** | MetaCubeXD 官方面板，自动铺 `config.js`，主题跟随路由器 |
| 🧩 | **配置生成** | 浏览器里选节点、定规则，生成 YAML 后写盘并 `mihomo -t` 校验 |
| 🌐 | **80 端口接入** | uhttpd 原生代理 / nginx / HAProxy 三条路自动选，失败自动回滚 |
| 🩺 | **自检与修复** | `doctor`、`status`、开机自检，固件升级后自动补齐 |
| 🔐 | **写入保护** | 载入配置前校验、失败不覆盖、写盘接口校验面板密码 |

## 一分钟装好

```sh
curl -fsSL https://mtun-xd.wxcircle.top/install.sh -o /tmp/mtun-xd-install.sh && sh /tmp/mtun-xd-install.sh
```

装完打开 LuCI → **服务 → 墨枢云境**。

> 从旧套件（`luci-app-mihomo-suite`）过来的机器，用无感迁移脚本：全程不重启内核，跑完自检「残留 = 0」。
>
> ```sh
> curl -fsSL https://mtun-xd.wxcircle.top/migrate.sh -o /tmp/migrate.sh && sh /tmp/migrate.sh
> ```

## 仓库

| 仓库 | 内容 |
| --- | --- |
| [OpenWrt-MTUN-XD](https://github.com/OpenWrt-MTUN-XD/OpenWrt-MTUN-XD) | 套件本体：LuCI 页面、套件脚本、配置工具、安装器 |
| [genkit](https://github.com/OpenWrt-MTUN-XD/genkit) | 配置工具的滚动发布包（套件「工具升级」从这里拉） |

## 常用命令

```sh
mtun-xd status      # 内核 / 面板 / 控制台 / 配置工具 一眼看完
mtun-xd doctor      # 环境自检
mtun-xd setup       # 补齐 / 修复整套（不覆盖配置）
mtun-xd core --bg   # 升级内核（后台，带回滚）
mtun-xd ui   --bg   # 升级面板
mtun-xd tool        # 更新配置工具
```

## 边界

- 只做「管理套件」：不修改 MetaCubeXD 的构建产物，也不替你决定节点与规则；
- 配置、工具密码、GEO 数据在卸载时默认保留，`uninstall --purge` 才彻底清；
- 内核与面板的版本跟随各自官方 Release，套件只负责装、校验、回滚。

<div align="center">
<br>

<sub>墨枢云境 · MTUN-XD　|　[MIT](https://github.com/OpenWrt-MTUN-XD/OpenWrt-MTUN-XD/blob/main/LICENSE)　|　[变更记录](https://github.com/OpenWrt-MTUN-XD/OpenWrt-MTUN-XD/blob/main/CHANGELOG.md)　|　[问题反馈](https://github.com/OpenWrt-MTUN-XD/OpenWrt-MTUN-XD/issues)</sub>

</div>
