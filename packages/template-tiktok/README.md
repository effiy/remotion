---
title: "Remotion TikTok Template"
tags: ["remotion", "template", "tiktok", "captioning", "whisper"]
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

A Remotion starter template tailored for TikTok-style video creation with built-in captioning support using Whisper.cpp for automatic speech-to-text subtitle generation.

---

## ⚡ 功能

- TikTok-optimized video template
- Automatic caption generation via Whisper.cpp
- Batch captioning of all videos in the `public` directory
- Configurable Whisper model selection
- Non-English language support via model configuration

---

## 📊 指标

「待补充」

---

## 🏛️ 设计

### Configure Whisper.cpp

Captioning will download Whisper.cpp and the 1.5GB big `medium.en` model. To configure which model is being used, you can configure the variables in `whisper-config.mjs`.

### Non-English languages

To support non-English languages, you need to change the `WHISPER_MODEL` variable in `whisper-config.mjs` to a model that does not have a `.en` suffix.

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
npm i
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

### Captioning

Replace the `sample-video.mp4` with your video file.
Caption all the videos in your `public` by running the following command:

```console
node sub.mjs
```

Only caption a specific video:

```console
node sub.mjs <path-to-video-file>
```

Only caption a specific folder:

```console
node sub.mjs <path-to-folder>
```

---

## ⚙️ 技术栈

「待补充」

---

## Docs

Get started with Remotion by reading the [fundamentals page](https://www.remotion.dev/docs/the-fundamentals).

## Help

We provide help on our [Discord server](https://remotion.dev/discord).

## Issues

Found an issue with Remotion? [File an issue here](https://github.com/remotion-dev/remotion/issues/new).

## License

Note that for some entities a company license is needed. [Read the terms here](https://github.com/remotion-dev/remotion/blob/main/LICENSE.md).