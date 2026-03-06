# 🎭 WeStud Login Animation

<p align="center">
  <a href="#english">English</a> · <a href="#中文">中文</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Pure-SVG%20%2B%20JS-6B4EFF?style=flat-square" />
  <img src="https://img.shields.io/badge/Dependencies-None-F5C518?style=flat-square" />
  <img src="https://img.shields.io/badge/License-MIT-F4782A?style=flat-square" />
  <img src="https://img.shields.io/badge/Single-File-1E1E1E?style=flat-square" />
</p>

---

## English

> A playful, character-driven login page where four geometric mascots **react emotionally** to your every interaction — built with pure SVG + vanilla JS, **zero dependencies**.

### ✨ Live Demo

Open `westud-login.html` directly in any modern browser. No build step. No server. No npm.

| Field | Value |
|-------|-------|
| Email | `test@westud.com` |
| Password | `123456` |

---

### 🎬 Character States

Four geometric mascots — **Purple Block**, **Black Block**, **Yellow Duck**, and **Orange Semicircle** — each express a distinct emotional state based on what the user is doing.

| State | Trigger | What happens |
|-------|---------|-------------|
| 🌊 **Idle** | Page load / no focus | Characters float gently, pupils follow mouse, random blinking |
| 👀 **Attentive** | Email field focused | Everyone leans forward, eyes snap wide open, pupils track mouse in real time |
| 🙈 **Shy** | Password field focused | Purple & orange avert gaze, yellow stares at ceiling, black goes half-lidded with a periodic sneaky peek |
| 😢 **Sad** | Wrong credentials | Purple tilts and droops, heavy eyelids, furrowed brows, sad mouths, whole scene shakes |
| 🎉 **Celebrate** | Login success | All characters jump with squash-and-stretch, arms raise, confetti bursts |

---

### 🏗️ Technical Architecture

#### Spring Physics Engine

All motion is driven by a custom `Spring` class — no CSS transitions, no tween libraries. Every animated value (position, rotation, opacity, pupil offset) owns its own spring instance.

```js
new Spring(stiffness, damping)
  .set(target)    // animate toward value
  .snap(value)    // instant placement, no animation
  .onChange = fn  // callback fires every frame
```

This produces naturally decelerating, overshoot-and-settle motion that feels hand-crafted rather than mechanical.

#### Pupil Tracking System

Seven pupils (2 purple · 2 black · 1 yellow · 2 orange) each have independent X/Y spring pairs. On every `mousemove`, screen coordinates are projected into SVG viewBox space and each spring targets the clamped direction vector — eyes organically lag behind the cursor.

#### State Machine

```
idle ←──────→ typing ←──────→ password
  ↑               ↓                ↓
  └────────── sad ←────────────────┘
                ↓
            success
```

`setState()` kills all pending timers and rAF loops before switching, preventing animation bleed between states.

#### SVG Layer Order (back → front)

```
1. Orange semicircle   — leftmost, background
2. Purple block        — tallest
3. Black block         — medium
4. Yellow duck         — rightmost, foreground
```

---

### 📁 File Structure

```
westud-login-animation/
├── westud-login.html   ← everything is here (SVG + CSS + JS, all inline)
└── README.md
```

---

### 🚀 Getting Started

```bash
git clone https://github.com/your-username/westud-login-animation.git
cd westud-login-animation
open westud-login.html        # macOS
# double-click on Windows / Linux
```

---

### 🛠️ Customization

**Change login credentials**
```js
const VALID = { email: 'you@example.com', pw: 'yourpassword' };
```

**Tune the spring feel**
```js
new Spring(300, 30)   // snappy
new Spring(180, 14)   // bouncy
new Spring(100, 28)   // slow and heavy
```

**Move characters**  
All characters live inside `viewBox="0 0 560 480"`. Adjust `x / y / width / height` on any `<rect>` or `<path>` to reposition.

---

### 🎨 Design Reference

Inspired by the **WeStud Creative Log-In** concept by [Outcrowd Studio](https://dribbble.com/shots/21953371-WeStud-Creative-Log-In-For-The-Educational-Platform) on Dribbble (July 2023).

| Character | Hex |
|-----------|-----|
| 🟣 Purple Block | `#6B4EFF` |
| ⚫ Black Block | `#1E1E1E` |
| 🟡 Yellow Duck | `#F5C518` |
| 🟠 Orange Circle | `#F4782A` |

---

### 📄 License

MIT — free for personal and commercial use.

<br/>

---
## 📞 Contact Information

If you have any questions or suggestions, please feel free to contact us:

- Email: 1583580876@qq.com  
- WeChat / Phone: +86 15267303402  

---

<div align="center">

**© Jintao Yang 2025 | westud-login-animation**

</div>


## 中文

> 一个充满趣味的角色驱动式登录页面，四个几何卡通人物会**随着用户操作实时做出情绪反应** —— 使用纯 SVG + 原生 JS 构建，**零依赖**。

### ✨ 在线演示

直接在任意现代浏览器中打开 `westud-login.html` 即可，无需构建、无需服务器、无需 npm。

| 字段 | 值 |
|------|-----|
| 邮箱 | `test@westud.com` |
| 密码 | `123456` |

---

### 🎬 角色状态说明

四个几何卡通角色 —— **紫色高块**、**黑色中块**、**黄色鸭嘴兽**、**橙色半圆** —— 根据用户当前操作，分别表现出不同的情绪状态。

| 状态 | 触发条件 | 角色表现 |
|------|----------|----------|
| 🌊 **空闲** | 页面加载 / 无焦点 | 轻微上下浮动、随机眨眼、瞳孔跟随鼠标 |
| 👀 **专注** | 点击邮箱输入框 | 全体前倾、眼睛猛地睁大、瞳孔实时追踪鼠标 |
| 🙈 **害羞** | 点击密码输入框 | 紫色和橙色回避视线，黄色望天，黑色半眯眼并定时偷瞟 |
| 😢 **难过** | 凭证错误 | 紫色歪斜下沉、眼皮下垂、眉头皱起、嘴角下撇、画面抖动 |
| 🎉 **庆祝** | 登录成功 | 四角色依次弹跳（含挤压拉伸）、双臂高举、五彩纸屑爆发 |

---

### 🏗️ 技术架构

#### 弹簧物理引擎

所有动画均由自研 `Spring` 类驱动 —— 不依赖 CSS transition，不依赖任何 tween 库。每个需要动画的属性（位移、旋转、透明度、瞳孔偏移）都拥有独立的弹簧实例。

```js
new Spring(刚度, 阻尼)
  .set(目标值)     // 弹簧动画到目标值
  .snap(值)        // 瞬间定位，无动画
  .onChange = fn   // 每帧触发的回调
```

弹簧物理产生的运动带有自然的减速和轻微过冲回弹，动感远胜于线性缓动。

#### 瞳孔追踪系统

七个瞳孔（紫色 ×2、黑色 ×2、黄色 ×1、橙色 ×2）各自拥有独立的 X/Y 弹簧对。每次 `mousemove` 事件触发时，屏幕坐标被投影至 SVG viewBox 空间，各弹簧以角度向量为目标，使眼珠自然地滞后于光标移动。

#### 状态机流转

```
空闲 ←──────→ 输入邮箱 ←──────→ 输入密码
  ↑               ↓                 ↓
  └────────── 登录失败 ←────────────┘
                  ↓
              登录成功
```

`setState()` 在切换状态前会清除所有计时器和动画帧，避免状态间的动画互相干扰。

#### SVG 图层顺序（从后到前）

```
1. 橙色半圆    — 最左侧，最底层
2. 紫色高块    — 最高
3. 黑色中块    — 中等高度
4. 黄色鸭嘴兽  — 最右侧，最前层
```

---

### 📁 文件结构

```
westud-login-animation/
├── westud-login.html   ← 所有代码都在这里（SVG + CSS + JS 全部内联）
└── README.md
```

---

### 🚀 快速开始

```bash
git clone https://github.com/your-username/westud-login-animation.git
cd westud-login-animation
open westud-login.html        # macOS
# Windows / Linux 直接双击文件即可
```

---

### 🛠️ 自定义配置

**修改登录凭证**
```js
const VALID = { email: 'you@example.com', pw: 'yourpassword' };
```

**调整弹簧手感**
```js
new Spring(300, 30)   // 快速弹回
new Spring(180, 14)   // 弹跳感强
new Spring(100, 28)   // 缓慢沉稳
```

**调整角色位置**  
所有角色在 `viewBox="0 0 560 480"` 坐标系内。修改对应 `<rect>` 或 `<path>` 的 `x / y / width / height` 属性即可重新定位。

---

### 🎨 设计参考

灵感来源：[Outcrowd Studio](https://dribbble.com/shots/21953371-WeStud-Creative-Log-In-For-The-Educational-Platform) 于 2023 年 7 月在 Dribbble 发布的 **WeStud Creative Log-In** 概念设计。

| 角色 | 颜色代码 |
|------|----------|
| 🟣 紫色高块 | `#6B4EFF` |
| ⚫ 黑色中块 | `#1E1E1E` |
| 🟡 黄色鸭嘴兽 | `#F5C518` |
| 🟠 橙色半圆 | `#F4782A` |

---

### 📄 开源协议

MIT —— 个人与商业项目均可免费使用。

---
## 📞 联系方式

如有任何疑问或建议，请随时联系我们：
- 邮箱: 1583580876@qq.com
- wechat/phone: 15267303402

---
<div align="center">

**©JintaoYang 2026 | westud-login-animation**

</div>
