# MCP 服务配置说明

## 通用约定

- `command` 用绝对路径，避免客户端 PATH 不同导致启动失败；
- 每个服务独立进程，崩溃只影响自己；
- 敏感信息（token、cookie、证书路径）一律走环境变量，不写进 JSON。

## frida-android

依赖：`frida`、`frida-tools`、设备上的 `frida-server`（版本必须与 PC 端一致）。

常见问题：

| 现象 | 处理 |
| --- | --- |
| `unable to connect to remote frida-server` | 检查 `adb forward tcp:27042 tcp:27042`、frida-server 是否运行 |
| attach 后进程崩溃 | 目标有反调试，先 `spawn` 再 hook，或延迟 attach |
| 版本不匹配 | `pip install frida==<server 版本>` |

## jadx-android

依赖：jadx（>= 1.5）。建议把 `JADX_DIR` 指向解压后的目录，而不是 GUI。

## x64dbg

依赖：x64dbg（x64/x32 对应目标位数）。`X64DBG_PATH` 指向安装目录。

注意：调试器需要与目标同位数；被调试进程有保护时先看 `docs/workflow.md`。

## js-reverse

依赖：Node 18+、Playwright/Chromium。用于浏览器端断点、网络请求、加密函数定位。

## camoufox-reverse

依赖：Camoufox（Firefox 内核）。适合有指纹检测的站点，抓包与 JS 观测优先用它。

## miniapp-reverse

依赖：微信 PC 端 + 调试端口（常见 62000）。先用 `list_targets` 确认 AppService/WebView 再 attach。
