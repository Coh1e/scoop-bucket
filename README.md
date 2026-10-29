# scoop-bucket

Coh1e 的 Windows 工具 Scoop bucket。

| 软件 | 说明 |
| --- | --- |
| `coop` | 与 Scoop 共用安装根、bucket 与安装记录的 Windows 原生软件包管理器 |
| `unsleep` | 极简 Windows 托盘防休眠工具 |

## 安装

```powershell
scoop bucket add coh1e https://github.com/Coh1e/scoop-bucket
scoop install coh1e/coop coh1e/unsleep
```

两个包都只发布 x64 产物，下载地址指向各自仓库 GitHub Release 的 `v<版本>` 标签。manifest 带有 `checkver` 与 `autoupdate`，上游发布新 tag 后按 `v$version` 拼出新的下载地址；SHA256 需要随版本更新。

## 维护

1. 上游推送 `v*` tag 后，Release 由各项目自己的 workflow 构建并附加 `*-x64.zip`。
2. 下载新资产，把 `version`、`url` 和 `hash` 写进 `bucket/<包名>.json`。
3. 在隔离的 Scoop 根里 `scoop install coh1e/<包名>` 验证后再提交。
