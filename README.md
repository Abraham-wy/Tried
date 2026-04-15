# 🌏 泰国曼谷旅游计划网站

一个仿苹果官网 UI 风格的静态旅游计划展示网站，包含完整的曼谷 + 芭提雅珊瑚岛行程、费用预算、演唱会贴士等内容。

**技术栈：** 纯 HTML + CSS + JavaScript，无任何依赖，单文件 `index.html`，可零配置部署到任意静态托管平台。

---

## 📋 目录

- [本地预览](#本地预览)
- [方案一：GitHub Pages（推荐）](#方案一github-pages推荐)
- [方案二：Vercel](#方案二vercel)
- [方案三：Netlify](#方案三netlify)
- [方案四：Cloudflare Pages](#方案四cloudflare-pages)
- [方案五：服务器 Nginx 部署](#方案五服务器-nginx-部署)
- [常见问题](#常见问题)

---

## 本地预览

无需安装任何依赖，直接在浏览器打开即可：

```bash
# 克隆仓库
git clone https://github.com/Abraham-wy/Tried.git
cd Tried

# 方法 A：直接双击 index.html 用浏览器打开

# 方法 B：用 Python 启动本地服务器（推荐，避免部分浏览器安全限制）
python3 -m http.server 8080
# 然后在浏览器访问 http://localhost:8080

# 方法 C：用 Node.js 的 npx serve
npx serve .
# 然后在浏览器访问 http://localhost:3000
```

---

## 方案一：GitHub Pages（推荐）

**优点：** 免费、无需服务器、与 GitHub 仓库直接集成、自动 HTTPS。

### 步骤

#### 1. 确认文件已推送到仓库

确保 `index.html` 在仓库根目录：

```
Tried/
├── index.html          ← 必须在根目录
├── README.md
└── 泰国曼谷旅游计划_赵露思演唱会.md
```

#### 2. 开启 GitHub Pages

1. 打开仓库页面：`https://github.com/Abraham-wy/Tried`
2. 点击顶部菜单 **Settings**（设置）
3. 左侧菜单找到 **Pages**（在 "Code and automation" 分组下）
4. 在 **Source** 下拉框中选择：
   - Branch：`main`（或你的主分支名）
   - 文件夹：`/ (root)`
5. 点击 **Save**

#### 3. 等待部署完成

约 1–3 分钟后，页面顶部会出现绿色提示：

```
Your site is live at https://abraham-wy.github.io/Tried/
```

点击链接即可访问你的网站 🎉

#### 4. 后续更新

每次 `git push` 到 `main` 分支，GitHub Pages 会**自动重新部署**，无需手动操作。

```bash
# 修改文件后
git add .
git commit -m "更新内容"
git push origin main
# 等待约 1 分钟后刷新网站即可看到更新
```

---

## 方案二：Vercel

**优点：** 部署极快（30 秒内）、全球 CDN 加速、自动 HTTPS、支持自定义域名。

### 方法 A：通过网页导入（最简单）

1. 打开 [vercel.com](https://vercel.com) 并用 GitHub 账号登录
2. 点击 **Add New → Project**
3. 找到 `Abraham-wy/Tried` 仓库，点击 **Import**
4. 配置页面保持默认（Framework Preset 选 `Other`）
5. 点击 **Deploy**

约 30 秒后，Vercel 会分配一个类似 `tried-xxx.vercel.app` 的域名。

### 方法 B：通过 Vercel CLI

```bash
# 安装 Vercel CLI
npm install -g vercel

# 在项目目录下运行
cd Tried
vercel

# 按提示操作：
# ? Set up and deploy "Tried"? → Y
# ? Which scope? → 选择你的账户
# ? Link to existing project? → N
# ? What's your project's name? → tried（或自定义名称）
# ? In which directory is your code located? → ./
# 部署完成后会输出访问 URL
```

---

## 方案三：Netlify

**优点：** 支持拖拽上传、表单处理、边缘函数，免费额度慷慨。

### 方法 A：拖拽上传（最快，无需账号注册 Git 绑定）

1. 打开 [app.netlify.com/drop](https://app.netlify.com/drop)
2. 将 `index.html` 文件（或整个项目文件夹）**直接拖入**页面中央区域
3. 等待约 10 秒，Netlify 自动分配一个 `xxx.netlify.app` 域名

### 方法 B：绑定 GitHub 仓库（推荐，支持自动更新）

1. 打开 [app.netlify.com](https://app.netlify.com) 并登录
2. 点击 **Add new site → Import an existing project**
3. 选择 **GitHub**，授权后找到 `Abraham-wy/Tried` 仓库
4. 配置：
   - Branch to deploy：`main`
   - Base directory：（留空）
   - Publish directory：`.`（英文句号，表示根目录）
5. 点击 **Deploy site**

每次推送到 `main` 分支后，Netlify 同样会自动重新部署。

---

## 方案四：Cloudflare Pages

**优点：** 全球 CDN 节点最多、无限带宽、免费计划非常慷慨。

1. 打开 [pages.cloudflare.com](https://pages.cloudflare.com) 并登录 Cloudflare 账号
2. 点击 **Create a project → Connect to Git**
3. 连接 GitHub，选择 `Abraham-wy/Tried` 仓库
4. 构建配置：
   - Framework preset：`None`
   - Build command：（留空）
   - Build output directory：`/`（或留空）
5. 点击 **Save and Deploy**

部署完成后访问 `https://tried.pages.dev`（或 Cloudflare 分配的域名）。

---

## 方案五：服务器 Nginx 部署

如果你有自己的云服务器（如阿里云、腾讯云），可以用 Nginx 部署。

### 步骤

```bash
# 1. 安装 Nginx（以 Ubuntu/Debian 为例）
sudo apt update
sudo apt install nginx -y

# 2. 将项目文件上传到服务器
# 方法 A：用 scp 上传
scp index.html user@your-server-ip:/var/www/html/

# 方法 B：在服务器上直接 git clone
cd /var/www/html
sudo git clone https://github.com/Abraham-wy/Tried.git .

# 3. 配置 Nginx
sudo nano /etc/nginx/sites-available/travel-site
```

在编辑器中粘贴以下配置：

```nginx
server {
    listen 80;
    server_name your-domain.com;  # 替换为你的域名或服务器 IP

    root /var/www/html;
    index index.html;

    location / {
        try_files $uri $uri/ /index.html;
    }

    # 开启 gzip 压缩提升加载速度
    gzip on;
    gzip_types text/html text/css application/javascript;
}
```

```bash
# 4. 启用站点配置
sudo ln -s /etc/nginx/sites-available/travel-site /etc/nginx/sites-enabled/
sudo nginx -t           # 检查配置是否正确
sudo systemctl reload nginx

# 5. 访问 http://your-server-ip 即可看到网站
```

### 配置 HTTPS（可选，推荐）

```bash
# 使用 Let's Encrypt 免费证书
sudo apt install certbot python3-certbot-nginx -y
sudo certbot --nginx -d your-domain.com
# 按提示填写邮箱，同意协议，Certbot 会自动完成 HTTPS 配置
```

---

## 自定义域名

所有平台均支持绑定自定义域名：

| 平台 | 设置入口 | 费用 |
|------|---------|------|
| GitHub Pages | Settings → Pages → Custom domain | 免费（需自备域名） |
| Vercel | Project → Settings → Domains | 免费（需自备域名） |
| Netlify | Site settings → Domain management | 免费（需自备域名） |
| Cloudflare Pages | Pages → Custom domains | 免费（需自备域名） |

域名购买推荐：[阿里云万网](https://wanwang.aliyun.com) / [腾讯云 DNSPod](https://dnspod.cloud.tencent.com) / [Namesilo](https://www.namesilo.com)（海外，价格低）

---

## 常见问题

**Q：打开网站显示空白？**  
A：检查 `index.html` 是否在仓库/部署的根目录。GitHub Pages 要求文件在 `/ (root)` 或 `/docs` 文件夹。

**Q：GitHub Pages 一直显示 404？**  
A：确认 Settings → Pages 的 Branch 已保存为 `main`，且分支上存在 `index.html`。有时需等待 3–5 分钟缓存刷新。

**Q：动画不流畅？**  
A：使用 Chrome / Safari / Edge 最新版本访问，旧版浏览器对 `backdrop-filter` 支持有限。

**Q：如何更新网站内容？**  
A：修改 `index.html` 后执行 `git add . && git commit -m "更新" && git push`，绑定了 GitHub 的平台会在 1–3 分钟内自动重新部署。

---

## 项目文件说明

```
Tried/
├── index.html                        # 🌐 网站主文件（单文件，无需其他依赖）
├── README.md                         # 📖 本说明文档
└── 泰国曼谷旅游计划_赵露思演唱会.md    # 📝 原始旅游计划 Markdown 文档
```

---

> 网站内容基于 2025 年 4 月方案，价格仅供参考，以实际出行时为准。
