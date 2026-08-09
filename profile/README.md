# ProjectArcturius

**Ether** —— 纯 Rust 自底向上构筑的 Wayland 空间桌面系统。

一个合成器、三枚原生壳应用、共享平台库与一套统一设计语言，全部以 Rust 编写。

---

## Ether —— 单一 monorepo

```
Ether/
├── compositor/      # Smithay 0.7 Wayland 合成器（wgpu/Vulkan + OpenGL ES 双后端）
├── librarian/       # 文件浏览器 + 桌面投影（eframe/egui）
├── launcher/        # Dock + Launchpad（SCTK + egui + wgpu）
├── settings/        # TopBar + 设置（raw wayland-client + fontdue + zbus）
├── shared/          # 平台库：ether-types / ether-assets / ether-ui / sokuou(submodule)
├── security-uniauth/ # 统一认证提权模块
└── kanesumi/        # Runtime（submodule，规划中）
```

各组件为独立进程：Librarian 持桌面投影（Layer 1）、Settings 持 TopBar（layer-shell TOP）、Launcher 持 Dock/Launchpad（BOTTOM/OVERLAY），合成器是唯一渲染权威，按固定层序合成。

## 设计语言与动画

- **Kanesumi（矩隅）** —— "以直角丈量边缘"。统一设计语言品牌，各平台为扇区：Ether 扇区主仓（Rust Runtime，mainline）· Android 扇区 `Kanesumi-sec-a`（Compose）。共享同一圆心：设计语言 + Sokuou 动画。
- **Sokuou（即応エンジン）** —— 进度驱动的 Rust 动画引擎。`SpringAnim` 解析解弹簧 · `UwpEasing` 全家族 · 可中断 `Progress`，零外部依赖。

## 设计原则

- **Metro 而非 Fluent** —— 轻盈、短促、0.25s、Quadratic/EaseOut
- **进度驱动动画**，非时间线；一切动画可中断
- **GPU 零重绘** —— 保留视觉树 + damage 局部重合成
- 纯色无渐变、直角几何、软件光标
- 系统空间主权 > 应用自治

## 技术栈

Rust · Smithay 0.7 · wgpu（Vulkan）/ OpenGL ES · Wayland · egui · resvg · fontdue · zbus

---

Takahashi Rinta —— [个人主页](https://takahashirinta.cn) · [GitHub](https://github.com/GuitaristRin)
