# 聘礼清单 · 囍

一个单文件、零构建的订婚聘礼清单页面：扫码 / 打开链接后是朱红礼堂大门，
**长按中央囍印蓄力，礼堂大门缓缓推开**，金光与花瓣中浮现「聘礼八大件」礼单：
金线手绘图标的首饰清单、¥ 金额数字滚动 + 大写金额、珍礼网格卡片，
页面底部还会**自动生成当前网址的二维码**，截图即可分享。

## 在线地址

https://huangjunhao9293.github.io/engagement-invite/

> 仓库：`huangjunhao9293/engagement-invite`（分支 `master`）。
> 页面底部二维码会自动按当前网址生成，换域名 / 改名后无需改代码。

## 文件说明

| 文件 | 说明 |
|---|---|
| `index.html` | 页面全部内容（HTML + CSS + JS 单文件） |
| `qrcode.min.js` | 二维码生成库（本地引用，部署时与 index.html 放同一目录） |

> 两个文件都要上传；缺了 `qrcode.min.js` 页面也能正常用，只是底部二维码位置会显示占位提示。

## 修改内容

用任意编辑器打开 `index.html`，只改顶部「★★★ 可修改区域 ★★★」即可：

```js
const CONFIG = {
  groom:  "黄俊豪",        // 男方姓名
  bride:  "龚胤僮",        // 女方姓名
  plaque: "我们订婚啦~",   // 门上匾额
  date:   "二〇二七 · 囍", // 日期
  holdMs: 900,             // 长按开门所需毫秒
  sound:  true             // 开门钟声
};

/* 礼单：type 三种
   jewel  → 首饰清单（icon 图标 + name 名称 + desc 祝福小字）
   money  → 礼金（amount 数字自动滚动 + cap 大写金额）
   simple → 珍礼网格卡（icon + title + sub） */
const CONFIG_SECTIONS = [ /* ... */ ];
```

图标可选：`bangle 手镯 / necklace 项链 / stud 耳钉 / chain 手链 / ring 戒指 /
diaring 钻戒 / diaring2 围镶钻戒 / pairring 对戒 / dianek 钻石项链 / ptstud 白金耳钉 /
phone 手机 / tea 茶 / quilt 被子 / chest 红箱`。

## 发布到 GitHub Pages（3 步）

1. 新建仓库（如 `engagement-invite`），把 `index.html` 和 `qrcode.min.js` 传上去：
   ```bash
   git init -b master && git add index.html qrcode.min.js
   git commit -m "聘礼清单"
   git remote add origin https://github.com/<你的用户名>/<仓库名>.git
   git push -u origin master
   ```
2. 仓库 → **Settings → Pages** → Source 选 `Deploy from a branch`，
   Branch 选 `master` / `/ (root)` → Save。
3. 等 1~2 分钟，访问
   `https://<你的用户名>.github.io/<仓库名>/`
   能看到大门即发布成功；此时页面底部会自动生成该网址的二维码。

> 提示：页面单文件自包含，也可以直接把两个文件通过微信发给别人双击打开
> （本地打开时底部二维码显示占位提示，属正常）。

## 二维码

- **别人扫你分享的码**：微信 / 浏览器扫任意二维码生成器里填入你的
  `https://<你的用户名>.github.io/<仓库名>/` 即可。
- **页面底部自带二维码**：部署后自动生成当前网址，长按即可保存转发。
- 小技巧：链接后面加 `#list`（如 `...github.io/<仓库名>/#list`）可跳过开门动画直达礼单，
  适合长辈或不想等动画的客人。

## 交互说明

- **长按** 中央囍印 → 蓄力圆环走满 → 大门缓缓推开（松手也会开门，不会卡住）
- 轻触任意位置也能直接开门（兜底，保证谁都能进去）
- 门开后礼单随滚动逐块浮现，礼金金额数字滚动，金色花瓣持续飘落
- 底部「重新开启大门」可重播动画
