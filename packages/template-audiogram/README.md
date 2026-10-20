---
title: "Remotion Audiogram Template"
tags: [remotion, template, audiogram, podcast, audio, captions]
category: template
created: "2026-10-20"
updated: "2026-10-20"
source: external
type: index
status: stable
lifecycle: active
---

# Remotion Audiogram Template

This template is for creating "audiograms". In other words, video clips from podcast episodes, or any other audio. It's a popular way of sharing audio snippets on social media.

[Example video](https://twitter.com/marcusstenbeck/status/1460641903326732300)

<p align="center">
  <img src="https://github.com/marcusstenbeck/remotion-template-audiogram/raw/main/Promo.png">
</p>

---

## 💡 概述

This template is for creating "audiograms" -- video clips from podcast episodes, or any other audio. It's a popular way of sharing audio snippets on social media.

---

## ⚡ 功能

- Generate captions using built-in transcription with `@remotion/install-whisper-cpp` or `@remotion/openai-whisper`
- Supply captions via `.srt` or `.json` (following `@remotion/captions` format)
- Support for long audio files with `useWindowedAudioData()` via `.wav` format
- Adjustable parameters in `src/Root.tsx` or Studio sidebar
- Customizable audio, cover art, and subtitles via the `public` folder

---

## 📊 指标

「待补充」

---

## 🏛️ 设计

「待补充」

---

## 📁 目录

「待补充」

---

## 🔗 资源

- [Remotion Documentation](https://www.remotion.dev/docs/the-fundamentals)
- [@remotion/captions](https://remotion.dev/docs/captions/caption)
- [@remotion/install-whisper-cpp](https://www.remotion.dev/docs/install-whisper-cpp/)
- [@remotion/openai-whisper](https://www.remotion.dev/docs/openai-whisper/openai-whisper-api-to-captions)
- [Discord Server](https://discord.gg/6VzzNDwUwV)
- [Issue Tracker](https://github.com/remotion-dev/remotion/issues/new)
- [Source (Monorepo)](https://github.com/remotion-dev/remotion/tree/main/packages/template-audiogram)
- [License](https://github.com/remotion-dev/remotion/blob/main/LICENSE.md)

---

## 🚀 快速开始

```
npm i
```

```
npx remotion studio
```

Start changing things like this:

- Adjust parameters in `src/Root.tsx` or in the Studio sidebar
- Replacing audio, cover and subtitles in the `public` folder

### Rendering

```console
npx remotion render
```

Or check out the [Remotion docs](/docs/render/). There are lots of ways to render.

### Generating captions

With the built-in transcription script using `@remotion/install-whisper-cpp`:

```console
bun transcribe.ts
# With Node.js: `npx tsx transcribe.ts`
```

This will:
- Ask for your audio file path (supports any ffmpeg format)
- Ask for the speech start time (to avoid false triggers from background music, intro jingles or noise)
- Generate captions.json in the public folder

Alternatively, use `@remotion/openai-whisper` to get captions from OpenAI Whisper into the right shape.

**Get it from a provider:**
- Your podcasting host might provide them for you.
- Descript makes transcription really easy.
- There are tons of other, paid solutions, like [Otter.ai](https://otter.ai), [Scriptme.io](https://scriptme.io) and [ListenRobo.com](https://listenrobo.com).

If you supply a .srt, make sure to export subtitles that are segmented by word rather than by sentence.

### Optimizing for long audio files

If your audio is long, make sure to pass a `.wav` file as audio.
The template will use `useWindowedAudioData()` to only fetch the data around the current time.
Otherwise, the waveform of the whole audio needs to be fetched, which may be slow.

---

## ⚙️ 技术栈

- Remotion
- TypeScript
- React
- `@remotion/captions`
- `@remotion/install-whisper-cpp` / `@remotion/openai-whisper` (captions)