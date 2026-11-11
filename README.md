# 个人作品下载站 · 使用说明

一共两个文件：

| 文件 | 作用 | 你以后要不要改 |
|---|---|---|
| `index.html` | 网页本身（排版、样式、功能） | **不用改**，放进仓库就别动了 |
| `data.js` | 你的名字、账号、全部作品 | **只改这个**，加作品就改它 |

另外 `preview/` 里是三张截图，不用上传。

托管 0 元，不需要服务器、不需要备案、不需要数据库。

---

## 一、上线（5 分钟，只做一次）

### 方式 A：GitHub Pages

1. 打开 [github.com](https://github.com) 登录，右上角 **+ → New repository**
2. 仓库名必须写成 **`你的用户名.github.io`**，可见性选 **Public**，Create
3. 进仓库 → **Add file → Upload files** → 把 `index.html` 和 `data.js` **两个**都拖进去 → **Commit changes**
4. 顶部 **Settings → Pages** → Source 选 **Deploy from a branch** → Branch 选 **main** + **/(root)** → **Save**
5. 等 1～2 分钟，打开 `https://你的用户名.github.io`

以后改内容**不需要重新走这 5 步**，见下面第二节。

### 方式 B：Cloudflare Pages（不用 Git，有时国内更快）

1. 注册 [dash.cloudflare.com](https://dash.cloudflare.com)
2. **Workers & Pages → Create → Pages → Upload assets**
3. 把 `index.html` + `data.js` 传上去 → **Deploy**
4. 得到 `https://xxxx.pages.dev`

> 想更稳一点就两个都部署：平时发 GitHub 的，别人说打不开就发 Cloudflare 的。

---

## 二、重点：上线以后怎么加新作品

网站的内容全部在 **`data.js`** 这个文件里，加作品就是**在这个文件里加一段文字**，然后提交。有两种做法，选一种就行。

### 做法 1：直接在 GitHub 网页上改（推荐，手机也能干）

1. 打开你的仓库，点 `data.js`
2. 右上角点**铅笔图标**（Edit this file）
3. 找到 `window.APPS = [` 这一段，翻到最后一个 `}` 的后面
4. **先打一个英文逗号 `,`**，然后把下面这段粘上去：

```js
{
  name: "新作品名字",
  tagline: "一句话说明",
  desc: "详细一点的介绍，一两句话就行。",
  icon: "N",
  tone: "green",
  version: "1.0.0",
  platforms: ["Windows"],
  size: "20 MB",
  quark: "https://pan.quark.cn/s/你的分享链接",
  quarkCode: "提取码",
  baidu: "",
  baiduCode: "",
  github: ""
}
```

5. 把里面的内容改成你自己的（**逗号、引号都别删**）
6. 页面往下拉，点绿色的 **Commit changes**
7. 等 1 分钟左右刷新网站，新作品就出现了

> GitHub 会记住每一次修改，改坏了可以点 **History** 回到上一版，不会丢。

### 做法 2：本地改完再上传

1. 用记事本 / VS Code 打开 `data.js`，按同样的方式加一段
2. 保存，双击 `index.html` 先看看效果
3. 回仓库 → **Add file → Upload files** → 把改好的 `data.js` 拖上去 → Commit（同名文件会直接覆盖）

### 三个必须注意的坑

- **逗号**：每个 `{ ... }` 之间用英文逗号隔开，**最后一段后面不要逗号**
- **引号**：都是英文双引号 `"`，从中文输入法打出来的 `"` 会让整个页面白掉
- **不想显示的东西就留空**：`baidu: ""` 就不显示百度按钮，`github: ""` 就不显示"查看源码"

### 删除作品

把对应的整段 `{ ... }`（连同后面的逗号）删掉就行，注意删完后最后一段别留逗号。

---

## 三、每个字段是什么意思

| 字段 | 说明 |
|---|---|
| `name` | 作品名字 |
| `tagline` | 一句话说明，显示在名字下面 |
| `desc` | 详细介绍，1～3 行 |
| `icon` | 图标：一个字母（如 `"D"`）或一个 emoji（如 `"🎮"`） |
| `tone` | 图标配色：`blue` `purple` `green` `orange` `pink` `gray` |
| `version` | 版本号，如 `"1.2.0"` |
| `platforms` | 支持的系统，如 `["Windows", "macOS"]`。写 2 种以上，页面顶部会自动出现筛选按钮 |
| `size` | 文件大小，如 `"12 MB"` |
| `quark` / `quarkCode` | 夸克网盘链接 / 提取码 |
| `baidu` / `baiduCode` | 百度网盘链接 / 提取码 |
| `github` | 这个作品的源码地址（可选） |

页头那三个按钮在上面的 `window.SITE` 里，改 `douyin` / `bilibili` / `github` 三个链接就行，哪个留空哪个就不显示。

---

## 四、网盘链接怎么拿

1. 把安装包（建议打包成 `.zip`）上传到夸克 / 百度网盘
2. 右键文件 → **分享** → 选"永久有效" → 复制链接
3. 链接长这样：
   - 夸克：`https://pan.quark.cn/s/xxxxxxxx`
   - 百度：`https://pan.baidu.com/s/1xxxxxxxx?pwd=abcd`
4. **百度的链接把 `?pwd=abcd` 一起复制**，别人点开会自动填好提取码

注意：必须是**分享链接**，不能是你自己网盘里的文件页地址；提取码区分大小写。

---

## 五、常见问题

**Q：加作品要重新部署吗？**
A：不用。GitHub Pages 会在你 commit 后 1 分钟左右自动重新发布，你只需要刷新网页。

**Q：想换成自己的图片当图标？**
A：在仓库里新建一个 `images` 文件夹，上传图片，然后 `icon: "images/xxx.png"`。

**Q：想换头像？**
A：现在头像是"名字的第一个字"。想用图片的话，把 `index.html` 里的 `<div class="avatar" id="avatar">` 换成 `<img class="avatar" src="images/avatar.jpg">`，然后在 CSS 的 `.avatar` 里加 `object-fit:cover`。

**Q：手机上看会不会很丑？**
A：已经做了响应式，手机上是单列大卡片，按钮也够大。

**Q：为什么别人打开有时候慢？**
A：GitHub Pages 在某些网络下会慢，可以同时部署一份 Cloudflare Pages 当备用链接。

**Q：要不要买域名？**
A：不需要。`你的用户名.github.io` 已经够用。想更好看就买个域名（`.com` 约 60–80 元/年），绑定方法：仓库 Settings → Pages → Custom domain 填进去，按提示加一条 CNAME 记录。用境外托管**不需要备案**。

---

## 六、成本

| 项目 | 费用 |
|---|---|
| 托管 | **0 元** |
| 存储（网盘） | **0 元** |
| 域名 | 0 元（免费二级域名）或 60–80 元/年 |
| **合计** | **0 元起** |
