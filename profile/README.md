# ProjectArcturius

**Arcturius 不止一个发行版** —— 以纯 Rust 自底向上的 Wayland 空间桌面系统 **Ether** 为轴，同时并行推进设计语言、动画引擎、原生客户端、游戏引擎与游戏，各自成仓。

主线 Ether：一个合成器、一组原生系统应用、共享平台库与一套统一设计语言，全部以 Rust 编写。

---

## Ether —— 单一 monorepo

```
Ether/
├── compositor/      # Smithay 0.7 Wayland 合成器（wgpu/Vulkan + OpenGL ES 双后端）
├── librarian/       # 文件浏览器 + 桌面投影（kanesumi-harness App）
├── launcher/        # Dock + Launchpad（kanesumi-harness App）
├── settings/        # TopBar + 设置中心（kanesumi-harness App + 服务层）
├── ceyboard/        # 输入法引擎（libime FFI + IME 候选窗）
├── chorus/          # 主题管理器（org.ether.Theme D-Bus）
├── repository/      # 包管理器 CLI（ether-manifest 审阅 + apt 交接）
├── security/uniauth/ # 统一认证提权（SUID root + vault）
├── shared/          # 平台库：ether-types / sokuou / ether-assets / ether-ui
│                    #        / ether-protocol / ether-manifest
└── kanesumi/        # Runtime（submodule：core/anim/canvas/structure/controls/harness）
```

各组件为独立进程：Librarian 持桌面投影（layer-shell Background）、Settings 持 TopBar（layer-shell TOP）、Launcher 持 Dock/Launchpad（Bottom/Overlay）、Ceyboard 持 IME 候选窗（Overlay）；合成器是唯一渲染权威，按固定层序合成，伴生进程热插拔自动重启。

## 设计语言与动画

- **Kanesumi Design（矩隅）** —— "以直角丈量边缘"。统一设计语言品牌，各平台为扇区：Ether 扇区主仓（Rust Runtime，mainline）· Android 扇区 `Kanesumi-sec-a`（Compose）。共享同一圆心：设计语言 + Sokuou 动画。
- **Sokuou（即応エンジン）** —— 进度驱动的 Rust 动画引擎。`SpringAnim` 解析解弹簧 · `UwpEasing` 全家族 · 可中断 `Progress`，零外部依赖。

## 设计原则

- **Kanesumi 而非 Fluent** —— 轻盈、短促、0.25s、Quadratic/EaseOut
- **进度驱动动画**，非时间线；一切动画可中断
- **GPU 零重绘** —— 保留视觉树 + damage 局部重合成
- 纯色无渐变、直角几何、软件光标
- 系统空间主权 > 应用自治

## 技术栈

Rust · Smithay 0.7 · wgpu（Vulkan）/ OpenGL ES · Wayland · kanesumi · sokuou · resvg · fontdue · zbus

---

## 其他产品线

- **[Arc Deck](https://github.com/ProjectArcturius/arc-deck)** —— DeepSeek Harness 的原生桌面客户端。两条实现路线并列：自绘 Rust（跨平台一致）与 WinUI 2（Windows 原生），共同出发点：彻底不用 WebView。
- **[Zethora Engine](https://github.com/ProjectArcturius/zethora-engine)** —— 用 Rust 编写的高性能现代游戏引擎。
- **[Galaxy on Fire Remake](https://github.com/ProjectArcturius/galaxy-on-fire-remake)** —— Rust + wgpu 重制《Galaxy on Fire 3D》（Fishlabs，Symbian 2010），覆盖 GOF1 完整功能集。非官方，与 Fishlabs 无关。
- **[Eclipse Souls](https://github.com/ProjectArcturius/eclipse-souls-docs)** —— 独立游戏，设定集文档仓库。
- **[ether-theme](https://github.com/ProjectArcturius/ether-theme)** —— Ether 系统主题资产：图标主题 + 光标主题（freedesktop / Xcursor）。

## 发布节奏：Arcturius Cycle

每半年一场，档期随学校假期——暑假一场（Solstice）、寒假一场（Equinox），内容三段：做了什么 · 做得怎么样 · 要做什么。命名约定与历届索引见 **[CYCLE.md](CYCLE.md)**（例：Arcturius Cycle IV Solstice，简写 `ac4s`）。

---

Takahashi Rinta —— [个人主页](https://takahashirinta.cn) · [GitHub](https://github.com/GuitaristRin)
