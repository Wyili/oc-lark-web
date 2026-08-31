# oc-lark 官网

这是 oc-lark 的产品官网与 GitHub Pages 静态落地页。当前为第二轮 UI 升级版（`web-refresh-02`），使用单文件 `index.html`，以产品官网节奏呈现品牌导航、Hero、终端窗口、核心能力、架构流程、私聊/群聊与审批交互、CLI 快速开始、本地 Web 控制台预览、开发版/正式版边界、FAQ 与 footer。

## 产品定位

oc-lark 是独立 Python 服务，连接飞书与原生 `opencode serve`，不替换 OpenCode 执行引擎，也不是云托管平台。已实现能力包括：

- 飞书 WebSocket 消息接收；私聊、群聊、topic/thread 上下文；
- OpenCode SSE 会话事件与实时输出回传；
- 卡片审批、选项与问询；
- 图片消息、会话关联、CLI 服务管理；
- 本地 Web 控制台的状态检查与通知入口。

页面中的聊天、终端、控制台和审批内容是前端展示演示，不代表真实后端返回值。

## GitHub Pages

仓库地址：<https://github.com/Wyili/oc-lark-web>

页面地址：<https://wyili.github.io/oc-lark-web/>

GitHub Pages 只静态托管 HTML/CSS/JavaScript，不会启动 Python 后端。页面无需安装前端依赖，可直接部署或自托管。

## 本地控制台与安全边界

页面保留 `API_BASE_URL` 和可选 Bearer token 输入，可通过浏览器运行时请求你自己的 `/api/status` 接口。输入值仅保留在当前页面内存中，刷新后清空；页面不会写入凭证。

使用本地控制台时：

- API 必须由你控制，并使用 HTTPS（本地开发可使用 localhost）；
- 后端自行实现认证、授权、CORS、速率限制和输入校验；
- token 应采用最小权限、短有效期，避免在公共电脑输入长期凭证；
- 飞书凭证、OpenCode 凭证和服务端密钥只能保存在后端环境变量或安全配置中；
- 不要把真实 token、内网地址或任何凭证写入页面或提交到仓库，也不要直接暴露 OpenCode Server。

## 本地开发

```bash
python -m http.server 8080
```

访问 <http://localhost:8080/>。修改后可用浏览器开发者工具检查响应式布局、滚动导航、移动菜单、命令复制、审批演示、FAQ 折叠和 API 状态检查交互。

项目不新增依赖，页面由单文件 HTML/CSS/JS 构成。