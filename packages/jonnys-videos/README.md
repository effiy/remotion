---
title: "Remotion Video (jonnys-videos)"
tags: ["remotion", "video", "hackathon", "roller-skis"]
category: "packages"
created: "2026-10-20"
updated: "2026-10-20"
source: "external"
type: "index"
status: "stable"
lifecycle: "active"
---

# Remotion video

<p align="center">
  <a href="https://github.com/remotion-dev/logo">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://github.com/remotion-dev/logo/raw/main/animated-logo-banner-dark.apng">
      <img alt="Animated Remotion Logo" src="https://github.com/remotion-dev/logo/raw/main/animated-logo-banner-light.gif">
    </picture>
  </a>
</p>

💡 概述

Welcome to your Remotion project!

---

⚡ 功能

- Roller ski video compositions in the `RollerSkis` folder
- Plane Sight hackathon video compositions in the `PlaneSight` folder
- Caption data and normalized audio management
- External media hosting via `remotion.media`

---

📊 指标

「待补充」

---

🏛️ 设计

「待补充」

---

📁 目录

「待补充」

---

🔗 资源

- Remotion fundamentals: [https://www.remotion.dev/docs/the-fundamentals](https://www.remotion.dev/docs/the-fundamentals)
- Discord server: [https://discord.gg/6VzzNDwUwV](https://discord.gg/6VzzNDwUwV)
- Issues: [https://github.com/remotion-dev/remotion/issues/new](https://github.com/remotion-dev/remotion/issues/new)
- License: [https://github.com/remotion-dev/remotion/blob/main/LICENSE.md](https://github.com/remotion-dev/remotion/blob/main/LICENSE.md)

---

🚀 快速开始

## Commands

**Install Dependencies**

```console
bun install
```

**Start Preview**

```console
bun run dev
```

**Render video**

```console
bunx remotion render
```

## Roller ski video

The compositions from the `roller-skis` project are in the `RollerSkis` folder in
Studio. Their source is in `src/roller-skis`, and the media is hosted under
`https://remotion.media/jonnys-videos/roller-skis/`. The caption data needed by
the rough cut is kept with the composition source.

## Plane Sight hackathon video

The `PlaneSight` folder in Studio contains `PlaneSightPromo` (97.7 seconds,
1280 × 720 at 30 fps) and its scene compositions. The source was copied from
[`mcbuehler/PlaneSight`'s `promo/` project](https://github.com/mcbuehler/PlaneSight/tree/a793a54732c1c3d1b7f7385c1113d70f4d9987be/promo),
created at the October 10, 2026 hackathon. The original cuts, captions, and
normalized audio are preserved. Media is hosted under
`https://remotion.media/jonnys-videos/plane-sight/`.

Run these commands from `packages/jonnys-videos`:

```console
bun run dev
bunx remotion render PlaneSightPromo out/plane-sight-promo.mp4
```

---

⚙️ 技术栈

- Remotion
- Bun