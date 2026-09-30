# 呆呆鸟 · dodobird.eu.org

不会飞，但一直在线。

单文件静态主页，无构建、无外部依赖。吉祥物是一只受了《鹅鸭杀》(Goose Goose Duck)
呆呆鸟启发、简化重绘的黄色呆鸟——对称放空的豆豆眼，和原角色"分头乱瞟"的眼神不一样。

## 文件

```
index.html            主页（内联动效：漂浮、眨眼、点击说话、投票彩蛋）
assets/
  dodo.svg            全身吉祥物（透明底，可任意放大）
  icon.svg            头像图标（透明底，作 favicon）
  icon-bg.svg         头像图标（奶黄色圆角底）
  icon-512.png        512×512，og:image / PWA
  icon-192.png        192×192
  apple-touch-icon.png  180×180，iOS 添加到主屏
  icon-32.png         32×32，常规 favicon 兜底
```

## sub2api 那边怎么用这套图标

把 `assets/` 里的图标拷过去，`<head>` 里加：

```html
<link rel="icon" type="image/svg+xml" href="/icon.svg">
<link rel="icon" type="image/png" sizes="32x32" href="/icon-32.png">
<link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">
```

## 部署

任选其一，都是纯静态：

- **GitHub Pages**：推到仓库，Settings → Pages → main 分支 / 根目录。
- **Cloudflare Pages**：连接仓库，构建命令留空，输出目录填 `/`。
- **和 sub2api 同机 nginx**：把整个目录拷到服务器，加一段 server/location 指到该目录即可：

```nginx
server {
    server_name dodobird.eu.org;
    root /var/www/dodobird;
    index index.html;
}
```

## 待办（上线路前）

- [ ] 把 `index.html` 里"联系"区的 GitHub / Email 占位链接换成真的。
- [ ] （可选）把 `og:image` 的相对路径换成绝对 URL，社交分享卡片更稳。

## 形象说明

吉祥物为简笔画风格的再创作：黄身、大白眼、垂嘴、黑描边与原角色神似，
但比例、眼神、线条均为重绘，非游戏官方素材。商用请谨慎，自用主页随意。
