# 李昀芷 · 转正答辩交互网页（线上部署版）

本文件夹是可直接上传到任何静态托管（Netlify / GitHub Pages / S3 等）的成品网站。

## 文件结构
```
李昀芷转正答辩线上版/
├── index.html      # 网站入口（默认页，访问根路径即打开；单文件内联 CSS+JS）
├── public/         # 全部图片素材（必须与 index.html 一起上传）
└── README-部署说明.md
```
> 图片按 `./public/...` 相对路径加载，所以 **index.html 和 public/ 必须放在同一目录上传**，缺一不可。

## 本地预览
```bash
cd 李昀芷转正答辩线上版
python3 -m http.server 8000
# 浏览器打开 http://localhost:8000/
```

## 当前线上部署（GitHub Pages）
- 线上网址：**https://ririyunzhi.github.io/liyunzhi-promotion-defense/**
- 仓库：github.com/ririyunzhi/liyunzhi-promotion-defense（分支 main，Pages 源 = main / 根目录）
- 最近一次更新：2026-10-12（Round 4：业绩页新增 KOL 项目业绩贡献模块；个人评价页更新个人待发展项；未来规划页新增「内部资源沉淀与跨项目复用」首模块）

## 修改网页后如何更新线上版本

### 方法 A（推荐，改完找我更新）
在本地 `promotion-defense-web` 项目改好 → 构建 `npm run build` → 把 `dist` 的新 `index.html` 与最新 `public/` 同步到本文件夹 → 让我把 `index.html` 推送回 GitHub 仓库即可。

### 方法 B（命令行）
```bash
# 1) 把仓库临时克隆出来并更新
git clone https://github.com/ririyunzhi/liyunzhi-promotion-defense.git ~/tmp/lyz-deploy
cd ~/tmp/lyz-deploy
cp /path/to/新index.html ./index.html
rsync -a /path/to/public/ ./public/
git add -A
git commit -m "deploy: update"
git push origin main   # 首次需要 GitHub 授权（浏览器登录一次）
```
> Push 后 GitHub Pages 会自动重新构建，约 1–2 分钟后生效。

### 方法 C（替代托管，无需 Git）
用鼠标把整个文件夹拖到 https://app.netlify.com/drop（需登录一次），即可得到 Netlify 公开链接。

## 注意
- 页面含公司业务数据（月度金额/成本/ROI、项目金额、预算规划等），对外分享前请确认范围。
- 网页为单机本地演示设计，部分交互数据保存于浏览器 localStorage，每位访问者看到的是默认版本。
