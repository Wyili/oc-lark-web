# oc-lark 官网

这是 oc-lark 的产品官网 / GitHub Pages 静态落地页，不是后端服务本身。页面使用单文件 `index.html`，包含产品定位、能力说明、架构流程、CLI 快速开始、聊天形态、实时输出、审批问询、图片消息、本地 Web 控制台、开发版资产分发、正式版规划、配置指南、演示和 FAQ。

## GitHub Pages

仓库地址：<https://github.com/Wyili/oc-lark-web>

启用 GitHub Pages 后，页面地址通常为：

<https://wyili.github.io/oc-lark-web/>

具体可访问地址以仓库 Settings → Pages 显示为准。

## 页面与本地 API 的关系

页面本身只托管静态 HTML/CSS/JavaScript，不包含 Python 后端，也不会在 GitHub Pages 上启动服务。官网展示的是完整产品能力；当前页面的演示流程是前端状态演示，不会伪造真实后端结果。

如果使用本地 Web 控制台能力，应将页面中的 `API_BASE_URL` 指向正在运行的 oc-lark Web API，并由后端提供对应的状态、会话、消息和通知接口。页面支持在控制台中配置 API 地址与 Bearer token 的入口（具体控制台实现可按后端 API 接入），但这些值只能用于浏览器运行时，不能写入 HTML 或提交到仓库。

后端安全要求：

- 必须使用 HTTPS（本地开发可使用 localhost）；
- 后端自行实现认证、授权、CORS、速率限制和输入校验；
- API token 使用最小权限、短有效期，并避免在公共电脑输入长期凭证；
- 飞书凭证、OpenCode 凭证及服务端密钥只能保存在后端环境变量或安全配置中；
- 不要把 `API_BASE_URL` 指向不受信任的服务，也不要在公开页面写入真实 token、内网地址或凭证。

## 本地开发

无需安装前端依赖。直接在仓库目录启动静态服务器即可：

```bash
python -m http.server 8080
```

然后访问 <http://localhost:8080/>。也可以直接打开 `index.html` 预览布局；使用静态服务器更接近 GitHub Pages 的运行方式。

本项目不新增依赖，页面由单文件 HTML/CSS/JS 构成，支持桌面和移动端响应式布局。修改后可用浏览器开发者工具检查锚点、命令复制、FAQ 折叠和状态演示交互。
