# 个人展示 Slidev

这是一个使用 [Slidev](https://sli.dev/) 制作的个人展示型 PPT/网页。

## 本地运行

```bash
cd portfolio
npm install
npm run dev
```

浏览器打开终端输出的地址。使用方向键、空格或点击左右区域翻页。

## 构建

```bash
npm run build
```

构建产物位于 `portfolio/dist/`。

## 修改个人信息

主要内容都在 `slides.md`：

- 搜索 `NIUAOYU` 修改姓名；
- 修改 GitHub 链接；
- 替换技能百分比与项目说明；
- 用自己的照片替换 `public/avatar.svg`，并同步修改图片引用；
- 在 `styles/index.css` 中修改配色和版式。

## GitHub Pages

仓库包含 `.github/workflows/deploy-portfolio.yml`。推送到 `main` 后，Action 会自动构建并发布。

第一次使用时，在 GitHub 仓库中进入：

`Settings → Pages → Build and deployment → Source → GitHub Actions`
