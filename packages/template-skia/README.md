---
title: "Remotion Skia Template"
tags: ["remotion", "template", "skia", "react-native-skia"]
category: "Template"
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

Welcome to your Remotion project!

---

## 💡 概述

A Remotion starter template with Skia (React Native Skia) integration, enabling 2D graphics rendering within Remotion compositions.

---

## ⚡ 功能

「待补充」

---

## 📊 指标

「待补充」

---

## 🏛️ 设计

### Using server-side rendering

This template uses a [custom Webpack override](https://www.remotion.dev/docs/bundlers). If you are using server-side rendering, you need to import `enableSkia` from `@remotion/skia/enable` and pass it to [`bundle()`](https://www.remotion.dev/docs/bundle) (if using SSR) and [`deploySite()`](https://www.remotion.dev/docs/lambda/deploysite) (if using Lambda):

```ts
bundle({
  entryPoint: entry,
  onProgress: () => undefined,
  webpackOverride: (config) => enableSkia(config),
});
// or
deploySite({
  webpackOverride: (config) => enableSkia(config),
});
```

---

## 📁 目录

「待补充」

---

## 🔗 资源

「待补充」

---

## 🚀 快速开始

**Install Dependencies**

```console
npm install
```

**Start Preview**

```console
npm run dev
```

**Render video**

```console
npx remotion render
```

**Upgrade Remotion**

```console
npx remotion upgrade
```

---

## ⚙️ 技术栈

「待补充」

---

## Docs

Get started with Remotion by reading the [fundamentals page](https://www.remotion.dev/docs/the-fundamentals).

## Help

We provide help [on our Discord server](https://discord.gg/6VzzNDwUwV).

## Issues

Found an issue with Remotion? [File an issue here](https://github.com/remotion-dev/remotion/issues/new).

## License

Note that for some entities a company license is needed. Read [the terms here](https://github.com/remotion-dev/remotion/blob/main/LICENSE.md).