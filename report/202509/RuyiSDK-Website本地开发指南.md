# RuyiSDK-Website 本地开发指南

本文档将指导您如何在本地环境中启动和运行 RuyiSDK 官方网站。

## 前置要求

在开始之前，请确保您的系统已安装以下软件：

- **Node.js** (版本 18.0 或更高)
- **npm** (通常随 Node.js 一起安装)
- **Git** (用于克隆代码仓库)

### 检查版本

打开终端或命令提示符，运行以下命令检查版本：

```bash
node --version  # 应显示 v18.0.0 或更高版本
npm --version   # 显示 npm 版本
```

## 快速开始

### 1. 克隆/下载项目

克隆项目：

```bash
git clone https://github.com/ruyisdk/ruyisdk-website.git	
cd ruyisdk-website
```

也可以在 github 上通过下载项目压缩包实现

### 2. 安装依赖

**推荐方式（更快、更可靠）：**
```bash
npm ci
```

**常规方式：**
```bash
npm install
```

> **提示**：`npm ci` 会根据 `package-lock.json` 文件进行精确安装，确保依赖版本完全一致，适合生产环境和团队协作。

### 3. 启动开发服务器

```bash
npm run dev
```

服务器启动后，在浏览器中访问 `http://localhost:3000` 即可查看网站。

## 常见问题及解决方案

### 问题 1: 404 页面错误

**现象**：浏览器显示"The requested path could not be found"

**原因**：开发服务器未正确启动或文档文件缺失

**解决方案**：
1. 确保在项目根目录运行命令
2. 检查终端是否有错误信息
3. 尝试重新安装依赖：`npm ci` 或 `npm install`

### 问题 2: 端口被占用

**现象**：提示"Something is already running on port 3000"

**解决方案**：
```bash
# 方法1：使用其他端口
npx docusaurus start --port 3001

# 方法2：停止占用端口的进程
# Windows:
netstat -ano | findstr :3000
taskkill /PID <进程ID> /F
```

### 问题 3: 文档版本错误

**现象**：提示"Docs version 'current' has no docs!"

**解决方案**：
1. 确保 `docs` 文件夹包含 `.md` 文件
2. 检查 `docusaurus.config.js` 配置是否正确

### 问题 4: 贡献者生成脚本超时

**现象**：`npm run dev` 命令卡在贡献者生成步骤

**解决方案**：
```bash
# 跳过贡献者生成，直接启动
npx docusaurus start
```

## 项目结构

```
ruyisdk-website/
├── docs/           # 文档源文件
├── blog/           # 博客文章
├── biweekly/       # 双周报
├── src/            # 源代码
├── static/         # 静态资源
├── i18n/          # 国际化文件
└── docusaurus.config.js  # 配置文件
```

## 开发命令

| 命令 | 说明 |
|------|------|
| `npm ci` | 精确安装依赖（推荐） |
| `npm install` | 安装依赖（常规方式） |
| `npm run dev` | 启动开发服务器（包含贡献者生成） |
| `npx docusaurus start` | 直接启动开发服务器 |
| `npm run build` | 构建生产版本 |
| `npm run serve` | 预览构建后的网站 |
| `npm run clear` | 清理缓存 |

## 编辑内容

- **文档**：编辑 `docs/` 目录下的 `.md` 或 `.mdx` 文件
- **博客**：编辑 `blog/` 目录下的文件
- **双周报**：编辑 `biweekly/` 目录下的文件
- **页面样式**：编辑 `src/css/` 目录下的样式文件

修改文件后，开发服务器会自动重新加载页面。

## 获取帮助

如果遇到问题，可以：

1. 查看项目的 [GitHub Issues](https://github.com/ruyisdk/ruyisdk-website/issues)
2. 参考 [Docusaurus 官方文档](https://docusaurus.io/docs)
3. 联系项目维护者

---

**提示**：首次启动可能需要几分钟时间来下载依赖和生成贡献者信息，请耐心等待。