# 李昀芷 · 转正答辩交互网页（线上部署版）

本文件夹是可直接上传到任何静态托管（Netlify / Pages / S3 等）的成品网站。

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

## 部署到 Netlify（推荐，无需命令行）
1. 浏览器打开 https://app.netlify.com/drop （首次会要求登录，可用 GitHub/邮箱账号）
2. 用鼠标把整个「李昀芷转正答辩线上版」文件夹拖进页面
3. 几秒后 Netlify 生成公开 HTTPS 链接，点击即可分享
4. 首次拖拽后会自动创建一个站点；之后可在 Netlify 站点后台管理

## 修改网页后如何更新线上版本
方法 A（最省事）：
1. 在本地项目改完 → 运行构建 `npm run build`（生成 dist）
2. 把新生成的 `index.html`（standalone）与最新 `public/` 同步到本文件夹
3. 重新拖拽整个文件夹到 https://app.netlify.com/drop （或在站点后台 Deploys 拖文件覆盖）

方法 B（命令行，需先安装并登录）：
```bash
npm i -g netlify-cli
netlify login          # 浏览器授权一次
netlify deploy --prod --dir="李昀芷转正答辩线上版"
```

## 注意
- 页面含公司业务数据（月度金额/成本/ROI、项目金额、预算规划等），对外分享前请确认范围。
- 网页为单机本地演示设计，部分交互数据保存于浏览器 localStorage，每位访问者看到的是默认版本。
