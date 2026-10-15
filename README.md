# 🎯 智能点名系统 · Smart Roll Call

一个高颜值、零依赖、开箱即用的课堂随机点名工具。支持自定义号数范围、多人同抽、不重复轮次、音效与粒子特效，所有数据自动保存在浏览器本地。

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
- 📋 **点名记录** — 实时显示最近点名历史，带时间戳
- 🏆 **被点排行** — 自动统计每个号数被点次数，Top 20 排行榜
- 🔊 **音效反馈** — 滚动音、中奖音，可一键静音
- ✨ **粒子特效** — 中奖瞬间 Canvas 粒子爆发，多人多段绽放
- 💾 **本地存储** — 名单、记录、设置自动保存，刷新不丢
- 📥 **批量导入** — 支持 `1-50`、`1,3,5,8-20` 等混合写法
- ⌨️ **快捷键** — 空格键开始点名，回车快速添加
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


candy535/535
├── index.html      # 完整应用（HTML + CSS + JS 单文件）
└── README.md       # 本文件
