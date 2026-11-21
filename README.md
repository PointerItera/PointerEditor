# PointerEditor

PointerEditor 是一个基于 TurboWarp scratch-gui 的蓝白主题 Scratch 兼容编辑器，包含桌面端、网页端、在线协作服务与移动端界面原型。

- 当前版本：0.3.0 Beta2（测试版，可能存在不稳定）
- 官网：<https://peditor.ctspace.xyz/>
- 网页版编辑器：<https://peditor.ctspace.xyz/editor/editor.html>
- 扩展商店：<https://peditor.ctspace.xyz/extensions/>
- 文档中心：<https://peditor.ctspace.xyz/docs/>
- 下载：<https://peditor.ctspace.xyz/#download> ｜ Releases：<https://github.com/PointerItera/PointerEditor/releases>
- 源码仓库：<https://github.com/PointerItera/PointerEditor>
- GitHub Pages 备份：<https://pointeritera.github.io/PointerEditor/>
- 原官网：<https://www.ctspace.xyz>

![PointerEditor 编辑器](docs/screenshots/editor.png)

## 功能

- **真实 Scratch 运行时**：复用 scratch-vm / scratch-blocks / scratch-paint / scratch-render / scratch-audio，支持积木、变量、列表、广播、克隆、造型、声音、扩展和作品运行。
- **蓝白主题与 OPPO Sans**：统一编辑器、菜单、弹窗、PEAgent 与扩展库的视觉。
- **PEAgent**：会话式 AI 助手，支持 DeepSeek V4、OpenAI 与自定义兼容模型，流式输出、Markdown、深度思考、网页搜索、选择积木、添加文件、会话持久化、操作预览与权限模式。
- **PointerEditor 扩展库**：全屏扩展页面，内置官方扩展与精选社区扩展；自带 Pointer 工具箱、Pointer 数学工具两个官方扩展，支持搜索、分类、一键安装与自定义加载。
- **PointerE 账号与协作**：注册、邮箱验证、积分、积分商城、TODO 房间同步、实时协作、角色认领与代码锁定。
- **创客次元发布**：桌面端可直接登录创客次元并发布作品。
- **Windows 文件关联**：注册 `.sb3` / `.sb2` / `.sb`，支持双击打开、`Ctrl+O` 打开、`Ctrl+S` 保存到原文件与 `Ctrl+Shift+S` 另存为。
- **PointerGuard 协作安全引擎**：实时监控异常锁定、整包同步轰炸和恶意清空；同步前自动保留本地快照，可一键回滚；校验协作项目完整性，协作中拒绝内嵌扩展。
- **多标签页与版本记录**：同一窗口打开多个作品，标签栏重命名/切换/关闭，每个标签自动保留最近 12 个快照并可恢复。
- **工作区背景自定义与深色主题**：支持预设、纯色与本地图片背景，可调背景模糊、面板模糊与透明度；深色背景会自动切换编辑器深色主题（顶栏、分类栏、舞台/角色面板、造型/声音资产区与全屏模式）。
- **云空间**：编辑器内直接上传、下载、重命名和删除云端 .sb3 作品与角色，角色卡片右键即可上传。
- **全部保存**：一次把所有标签页导出为独立 .sb3 文件。
- **圆角矩形**：画图工具栏新增圆角矩形，圆角半径 0–80 可调。
- **多窗口与跨窗口素材**：新建窗口、角色卡片拖拽到另一个窗口。

![PEAgent](docs/screenshots/agent.png)

![扩展库](docs/screenshots/extensions.png)

## 下载

0.3.0 Beta2 安装包、免安装版与网页版静态包：

国内官方节点（下载更快）：

- Windows 安装版：<https://vable.ctspace.xyz/downloads/PointerEditor-0.3.0-Beta2-setup.exe>
- Windows 免安装版：<https://vable.ctspace.xyz/downloads/PointerEditor-0.3.0-Beta2-win64.zip>
- 网页版静态包：<https://vable.ctspace.xyz/downloads/PointerEditor-0.3.0-Beta2-web.zip>

GitHub Releases（海外 / 备用）：

- Windows 安装版：[PointerEditor-0.3.0-Beta2-setup.exe](https://github.com/PointerItera/PointerEditor/releases/download/v0.3.0-beta.2/PointerEditor-0.3.0-Beta2-setup.exe)
- Windows 免安装版：[PointerEditor-0.3.0-Beta2-win64.zip](https://github.com/PointerItera/PointerEditor/releases/download/v0.3.0-beta.2/PointerEditor-0.3.0-Beta2-win64.zip)
- 网页版静态包：[PointerEditor-0.3.0-Beta2-web.zip](https://github.com/PointerItera/PointerEditor/releases/download/v0.3.0-beta.2/PointerEditor-0.3.0-Beta2-web.zip)
- Release 页面：<https://github.com/PointerItera/PointerEditor/releases/tag/v0.3.0-beta.2>
- 在线使用：<https://peditor.ctspace.xyz/editor/editor.html>

## 目录结构

```
scratch-gui/     Scratch 编辑器前端（React / Redux / webpack）
shell/           Electron 桌面外壳、PEAgent 主进程、Windows 安装器配置
collab-server/   PointerE 账号、积分、TODO 与 WebSocket 协作服务
website/         官网静态页
mobile/          移动端界面原型（不含 APK）
docs/            扩展库 GitHub Pages 页面、截图与说明
```

## 本地开发

要求 Node.js 20+。首次安装依赖：

```bash
cd scratch-gui
npm ci

cd ../shell
npm ci

cd ../collab-server
npm ci
```

### 编辑器前端

```bash
cd scratch-gui
npm start          # webpack-dev-server
# 或
npm run build      # 输出到 scratch-gui/build
```

### 桌面端

先构建 `scratch-gui/build`，然后：

```bash
cd shell
npm start
```

打包 Windows 安装器：

```bash
cd shell
npx electron-builder --win nsis --x64
```

桌面版会把项目数据与导出文件放在程序目录的 `PointerEditorData` 和 `PointerEditorExports` 中。

### 协作服务

```bash
cd collab-server
POINTER_DATA_DIR=./data POINTER_PUBLIC_URL=https://example.com npm start
```

默认端口 `8788`。自托管时请设置：

- `POINTER_ADMIN_USER` / `POINTER_ADMIN_PASSWORD`
- `POINTER_SMTP_HOST` / `POINTER_SMTP_PORT` / `POINTER_SMTP_USER` / `POINTER_SMTP_PASS`
- 管理入口在开源副本中为 `/pointere-console`，部署前请同步修改 `server.cjs`、`public/admin.html` 与 `public/admin.js` 中的路径。

仓库不包含任何账号数据库、SMTP 授权码、管理员密码、用户作品或运行数据。

## PEAgent

PEAgent 的模型 API Key 仅保存在本机，由 Electron `safeStorage` 加密；请求直接发送到用户填写的模型接口，不经过 PointerE 服务器。

桌面端默认预填 DeepSeek V4 服务地址与 `deepseek-flash` / `deepseek-v4-pro` 模型，也可以切换 OpenAI 或任何 OpenAI / Anthropic 兼容接口。

## 扩展库

编辑器内点击积木区左下角「添加扩展」即可打开全屏扩展库：

- **官方扩展**：Scratch 内置的音乐、画笔、视频侦测、文字朗读、翻译、硬件扩展等。
- **Pointer 精选**：PointerEditor 官方维护的 Pointer 工具箱、Pointer 数学工具。
- **社区精选**：由社区作者维护的扩展，安装时从扩展的官方地址加载。

GitHub Pages 版本：<https://pointeritera.github.io/PointerEditor/extensions/>

## 安全说明

- 不会在客户端硬编码模型 API Key、SMTP 授权码或管理员密码。
- 协作服务对 HTTP / WebSocket 做 Origin 校验、频率限制、请求体校验与安全响应头。
- 扩展加载前由安全管理器校验来源；自定义扩展需要用户确认。
- Agent 不执行任意 JavaScript，变量、广播、积木和 SVG 操作均在本地校验后应用。
- 如果你发现安全问题，请不要在公开 Issue 中贴出利用细节，先联系维护者。

## 许可

本项目整体以 **GNU GPL v3** 分发，见 [LICENSE](LICENSE)。上游 TurboWarp scratch-gui 同样使用 GPL-3.0；Scratch 是 MIT 的商标，本项目与 MIT / Scratch 团队无隶属关系。

第三方组件、字体、社区扩展与 Blockly 的许可见 [NOTICE.md](NOTICE.md) 及各子目录中的 LICENSE 文件。
