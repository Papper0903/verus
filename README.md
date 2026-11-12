# 缜理 · VERUS

一个像素风的个人主页：低分辨率的夜空、三张像素报纸、一枚绕着星星的月亮。

- 首屏：《偷影子的人》式的静夜——山脊、月亮、几个没有主人的影子，全部用 canvas 逐像素画出来
- 三段报纸：**About me** / **个人推荐作品** / **learn about me**，像素边框 + 硬阴影 + 抖动网点
- 结尾：96×96 的像素月亮放大到 480px，一圈星星绕着它转
- 全站有像素小星星缓缓飘落

## 文件

```
index.html     整站（HTML / CSS / JS 全部内联，无构建、无依赖安装）
fonts/         Zpix（中文像素字，966 KB）、Silkscreen（拉丁像素字）
preview.png    首屏预览图（README 用，可删）
README.md      本文件
```

> 上传时请把 `fonts/` 一起传上去，否则中文会退回系统宋体，像素感就没了。

## 本地查看

直接双击 `index.html`。

## 上传到 GitHub Pages

1. 新建仓库（例如 `verus`）。
2. **Add file → Upload files**，把 `index.html`、`fonts/`、`README.md`、`preview.png` 拖进去 → Commit。
3. **Settings → Pages → Build and deployment**
   - Source：`Deploy from a branch`
   - Branch：`main`，目录 `/ (root)` → **Save**
4. 等 1–2 分钟，访问 `https://<用户名>.github.io/<仓库名>/`。

命令行：

```bash
cd verus-site
git init
git add .
git commit -m "verus site"
git branch -M main
git remote add origin git@github.com:<用户名>/<仓库名>.git
git push -u origin main
```

## 想改内容时搜这些词

| 要改什么 | 搜索关键词 |
| --- | --- |
| 名字 / 英文名 | `缜理`、`VERUS` |
| 生日 | `070903`、`2003.07.09`、`07 · 09 · 03` |
| 自我描述 | `主观唯心主义者` |
| 签名 | `获得幸福吧`、`MAY YOU BE HAPPY` |
| 三件作品 | `class="card"`，卡片里的 `<a class="go" href="...">` 是链接 |
| 封面图 | `data-art="book|song|soul"`，对应 JS 里的 `drawBook / drawSong / drawSoul` |
| 微信 / QQ | `zhenli09_03`、`2183465142`（按钮的 `data-copy` 要一起改） |
| 结尾文案 | `月亮升起来了` |
| 首屏文案 | `NO.0903`、`的夜航` |

## 像素是怎么做出来的

- **首屏**：canvas 只有约 360×225（手机约 130×281），每 1 格放大成 4 个（或 3 个）屏幕像素，所以边缘是硬的。天空用 5 段色带 + 有序抖动过渡，月亮是三档颜色 + 棋盘抖动的明暗交界，山脊用正弦曲线取整后逐列填色。
- **结尾月亮**：96×96 的 canvas 放大 5 倍，同一套画月亮的函数，外加 60 个静态星点 + 34 颗绕行星星。
- **封面**：64×86 的 canvas 画完再交给 CSS 放大，三张分别是《偷影子的人》的月夜山坡、单曲的金色光球、Soul 的火花与琴键。
- **报纸**：奶油纸色 + 3px 硬边框 + `10px 10px 0` 的硬阴影，叠一层 2px 的棋盘网点，全站没有一处圆角或模糊。
- **字体**：Zpix 是 12px 的中文点阵字体，所以正文 12px、标题 24/36/48/72/96px 都是它的整数倍，放大才不发虚。

## 一点提醒

微信号 `zhenli09_03` 和 QQ `2183465142` 是明文写在页面里的，任何人打开源码都能看到，也容易被爬。如果之后觉得打扰，可以换成图片、邮箱，或者加一层「点击显示」。
