# 🎯 智能抽号数系统 · Smart Roll Call

一个高颜值、零依赖、开箱即用的课堂随机点名工具。支持自定义号数范围、多人同抽、不重复轮次、手动停止、音效与粒子特效，所有数据自动保存在浏览器本地。

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![Dependencies](https://img.shields.io/badge/Dependencies-0-brightgreen?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)

---

## ✨ 特性

- 🔢 **号数范围自定义** — 起始号、结束号任意填（1-999），一键生成名单
- 🎲 **多人同抽** — 一次可抽 1-10 个号，同时滚动、依次定格
- 🔁 **不重复模式** — 每轮优先抽没被点过的号数，全部点完自动开启下一轮
- 🛑 **手动停止模式** — 无限滚动，点击按钮或按空格随时定格结果
- 📋 **点名记录** — 实时显示最近点名历史，带时间戳
- 🏆 **被点排行** — 自动统计每个号数被点次数，Top 20 排行榜
- 🔊 **音效反馈** — 滚动音、中奖音，可一键静音
- ✨ **粒子特效** — 中奖瞬间 Canvas 粒子爆发，多人多段绽放
- 💾 **本地存储** — 名单、记录、设置自动保存，刷新不丢
- 📥 **批量导入** — 支持 `1-50`、`1,3,5,8-20` 等混合写法
- ⌨️ **快捷键** — 空格键开始点名 / 停止，回车快速添加
- 📱 **响应式** — 桌面、平板、手机自适应

---

## 🚀 快速开始

**方式一：直接打开**

下载 `index.html`，双击用浏览器打开即可。

**方式二：本地服务器**

```bash
npx serve .
# 或
python -m http.server 8080
```

**方式三：在线体验**

访问 GitHub Pages 部署地址:https://candy535.github.io/535/

---

## 📖 使用说明

### 1. 生成名单

在左侧面板的「号数范围」中输入起始号与结束号（例如 `1` 到 `40`），点击 **生成名单**。

> ⚠️ 若当前已有名单，会提示确认替换，并清空点名记录。

### 2. 补加 / 删除单个号数

- 在输入框输入号数后按 **回车** 或点击 **+** 按钮即可补加
- 鼠标悬停在列表项上，点击右侧 **×** 可删除该号数

### 3. 批量导入

点击左下角 **批量导入**，支持以下写法：

```text
1-50
1,3,5,8-20
1 2 3 4 5
1，3，5
```

也支持顿号、分号等分隔符。

### 4. 开始点名

- 点击中央 **开始点名** 按钮，或直接按 **空格键**
- 默认 **自动模式**：滚动约 3 秒后自动定格（滚动期间按钮禁用）
- 开启 **手动停止** 后：持续滚动，点击 **停止** 按钮或按 **空格键** 才定格
- 抽取个数通过 `− / +` 调节，范围 **1 ~ 10**

### 5. 模式开关

| 开关 | 说明 |
| --- | --- |
| 不重复模式 | 优先抽取本轮未被点过的号数；抽完自动进入下一轮 |
| 手动停止 | 无限滚动，需手动点击停止才出结果 |
| 音效开关（右上角 🔊） | 控制滚动音与中奖音效 |

### 6. 清空记录

点击 **清空记录** 可重置所有号数的被点次数与历史记录（**名单保留**）。

---

## 🎨 界面结构

```text
┌──────────────────────────────────────────────────────────┐
│  ✦ 智能点名系统            总号数 / 已点名 / 剩余 / 轮次  🔊 │
├────────────┬────────────────────────────┬────────────────┤
│  号数名单   │                            │   点名记录      │
│  ─────────  │        结果展示区           │   ──────────    │
│  号数范围   │      （滚动 / 定格）        │   被点排行      │
│  单个补加   │                            │                │
│  列表 + ×   │   [ 开始点名 ]  抽取 1 个    │                │
│  批量/清空  │   不重复 · 手动停止          │                │
└────────────┴────────────────────────────┴────────────────┘
```

---

## 🧩 技术实现

| 模块 | 说明 |
| --- | --- |
| 抽取算法 | Fisher–Yates 部分洗牌，`O(n)` 无偏抽样 |
| 滚动动画 | 递归 `setTimeout`，间隔按 `p³·²` 曲线递增，模拟减速手感 |
| 手动停止 | 无限滚动循环，用户点击后立即调用 `stopRoll()` 定格 |
| 结果渲染 | CSS 变量 `--size` 动态缩放，`--i` 控制错峰入场延迟 |
| 粒子系统 | Canvas 2D + `requestAnimationFrame`，矩形/圆形混合粒子 |
| 音效 | Web Audio API 振荡器实时合成，无外部音频文件 |
| 持久化 | `localStorage`，Key = `smart-rollcall-num-v5` |
| 兼容处理 | `webkitAudioContext`、`backdrop-filter` 降级 |

---

## 🌐 浏览器支持

| 浏览器 | 版本 |
| --- | --- |
| Chrome / Edge | 88+ |
| Firefox | 90+ |
| Safari | 15+ |
| 移动端浏览器 | iOS Safari 15+ / Chrome Android 90+ |

> 音效需在用户首次交互后才能播放（浏览器自动播放策略），本项目已在首次点击/按键时自动初始化音频上下文。

---

## 🗂 项目结构

```text
.
├── index.html      # 单文件应用（HTML + CSS + JS 全内联）
└── README.md       # 项目说明
```

> 整个项目 **仅一个 HTML 文件**，无构建、无依赖、无 CDN 请求，复制即用。

---

## 🔧 可调参数

打开 `index.html`，在 `<script>` 顶部可调整：

```js
const MAX_NUM = 999;       // 单个号数上限
const DEFAULT_START = 1;   // 默认起始号
const DEFAULT_END = 40;    // 默认结束号
const MAX_PICK = 10;       // 一次最多抽取个数
const duration = 3000;     // 自动模式滚动时长（毫秒）
```

---

## 📌 常见问题

**Q：刷新后数据会丢失吗？**

A：不会。名单、记录、轮次与所有开关状态都会保存在浏览器本地。

**Q：为什么没有声音？**

A：请先与页面产生一次交互（点击或按键），并确认右上角音效按钮为 🔊 状态。

**Q：如何重置全部数据？**

A：点击「清空记录」重置次数与历史；或清除浏览器站点数据彻底重置。

**Q：能抽学号以外的内容吗？**

A：目前以号数为主。批量导入支持任意 `1-999` 的数字。

**Q：手动停止和自动模式有什么区别？**

A：自动模式滚动约 3 秒后自动定格；手动停止模式会一直滚动，直到你点击「停止」或按空格键。

---

## 🤝 贡献

欢迎提交 Issue 与 Pull Request！

1. Fork 本仓库
2. 新建分支 `git checkout -b feature/your-feature`
3. 提交改动 `git commit -m "feat: add something"`
4. 推送分支 `git push origin feature/your-feature`
5. 打开 Pull Request

---

## ⭐ 支持一下

如果这个项目对你有帮助，欢迎点个 **Star** ⭐ 或在 GitHub 上关注我们。

你的每一个 Star，都是持续更新的动力 ❤️

[![Star this repo](https://img.shields.io/badge/⭐-Star%20this%20repo-fbbf24?style=for-the-badge)](https://github.com/)
[![Follow on GitHub](https://img.shields.io/badge/GitHub-Follow-181717?style=for-the-badge&logo=github)](https://github.com/)

---

## 📄 License

本项目基于 **MIT License** 开源，可自由用于教学、商用与二次开发。

---

<div align="center">

**Made with ❤️ for teachers and students.**

</div>
