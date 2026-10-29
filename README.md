# mcp-and-skills-pack

把日常逆向/安全分析用到的 **MCP 服务配置** 与 **技能清单** 整理成可直接复用的模板：不绑定具体工具实现，只保留配置结构、占位符和使用方法。

> 仅用于自己拥有或获得授权的目标；仓库内不含任何账号、密钥、证书或客户数据。

## 目录

```
mcp/
  servers.example.json     MCP 服务配置模板（路径与密钥全部占位）
  README.md                每个服务的用途、依赖、常见坑
skills/
  README.md                技能清单：名称 / 用途 / 触发词 / 适用阶段
docs/
  workflow.md              逆向工作流：取证 → 静态 → 动态 → 复现 → 记录
```

## 快速开始

1. 复制配置模板：

```bash
cp mcp/servers.example.json ~/.config/mcp/servers.json
```

2. 把里面的 `REPLACE_ME` 替换成本机路径：

| 占位符 | 含义 |
| --- | --- |
| `PYTHON_EXE` | Python 解释器绝对路径 |
| `NODE_EXE` | Node 可执行文件路径 |
| `JADX_DIR` | jadx 安装目录 |
| `X64DBG_DIR` | x64dbg 安装目录 |
| `FRIDA_HOST` | frida-server 地址（USB 可留空） |

3. 重启你的 AI 客户端，确认 MCP 服务已加载。

## 包含的服务类型

| 服务 | 用途 |
| --- | --- |
| `frida-android` | Android 运行时 Hook、内存读写、类枚举 |
| `jadx-android` | 反编译结果查询、方法/字段定位 |
| `x64dbg` | Windows 调试：断点、寄存器、内存、调用栈 |
| `js-reverse` | 浏览器端 JS 调试、断点、网络请求分析 |
| `camoufox-reverse` | 反检测浏览器下的 JS 逆向与指纹观测 |
| `miniapp-reverse` | 小程序/WebView CDP 调试 |

## 安全

- `servers.json` 不要提交到仓库；本仓库只提供 `*.example.json`；
- 任何 token、cookie、证书一律用环境变量注入；
- 工具仅用于授权测试与自有应用分析。

## License

MIT
