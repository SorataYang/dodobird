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

已托管在 **GitHub Pages**（仓库 [SorataYang/dodobird](https://github.com/SorataYang/dodobird)，main 分支根目录），绑定域名 `www.dodobird.eu.org`。更新主页 = 改完代码 push 到 main，一分钟内自动上线。

域名解析（Cloudflare）还需加一条记录，加完即生效：

| 类型 | 名称 | 目标 | 代理 |
| ---- | ---- | ---- | ---- |
| CNAME | www | SorataYang.github.io | 仅 DNS（灰云） |

> 灰云让 GitHub 直接签发 HTTPS 证书；证书下来后想套 CF 也可以再开橙云。
> 若日后想把主域 `dodobird.eu.org` 也指过来：先确认主域上的服务已迁走，然后在 Cloudflare 加 CNAME `@ → SorataYang.github.io`（Cloudflare 会做 CNAME 压平），并把仓库 CNAME 文件和 Pages 设置里的域名改成主域。

本地预览：`python3 -m http.server 8899`，浏览器开 `http://127.0.0.1:8899`。

## 待办（上线路前）

- [ ] 把 `index.html` 里"联系"区的 GitHub / Email 占位链接换成真的。
- [ ] （可选）把 `og:image` 的相对路径换成绝对 URL，社交分享卡片更稳。

## 形象说明

吉祥物为简笔画风格的再创作：黄身、大白眼、垂嘴、黑描边与原角色神似，
但比例、眼神、线条均为重绘，非游戏官方素材。商用请谨慎，自用主页随意。
