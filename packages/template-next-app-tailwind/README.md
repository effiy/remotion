---
title: "Remotion Next.js App Tailwind Template"
tags: [remotion, template, nextjs, tailwindcss, lambda, player]
category: template
created: "2026-10-20"
updated: "2026-10-20"
source: external
type: index
status: stable
lifecycle: active
---

# Remotion Next.js App Tailwind Template

<img src="https://github.com/remotion-dev/template-next/assets/1629785/9092db5f-7c0c-4d38-97c4-5f5a61f5cc098" />
<br/>
<br/>

This is a Next.js template for building programmatic video apps, with [`@remotion/player`](https://remotion.dev/player) and [`@remotion/lambda`](https://remotion.dev/lambda) built in.

Tailwind CSS is included.

<img src="https://github.com/remotion-dev/template-next/assets/1629785/c9c2e5ca-2637-4ec8-8e40-a8feb5740d88" />

---

## 💡 概述

This is a Next.js template for building programmatic video apps, with `@remotion/player` and `@remotion/lambda` built in. Tailwind CSS is included.

---

## ⚡ 功能

- Next.js App Router with Remotion integration
- `@remotion/player` for in-browser video playback
- `@remotion/lambda` for serverless rendering on AWS
- Tailwind CSS for styling
- Deployable to AWS Lambda via `deploy.mjs`

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

- [Remotion Fundamentals](https://www.remotion.dev/docs/the-fundamentals)
- [Remotion Lambda Setup](https://www.remotion.dev/docs/lambda/setup)
- [Discord Server](https://remotion.dev/discord)
- [Issue Tracker](https://remotion.dev/issue)
- [License](https://github.com/remotion-dev/remotion/blob/main/LICENSE.md)

---

## 🚀 快速开始

### Getting Started

[Use this template](https://github.com/new?template_name=template-next-app-dir-tailwind&template_owner=remotion-dev) to clone it into your GitHub account. Run

```
npm i
```

afterwards. Alternatively, use this command to scaffold a project:

```
npx create-video@latest --next
```

### Commands

Start the Next.js dev server:

```
npm run dev
```

Open the Remotion Studio:

```
npx remotion studio
```

Render a video locally:

```
npx remotion render
```

Upgrade Remotion:

```
npx remotion upgrade
```

The following script will set up your Remotion Bundle and Lambda function on AWS:

```
node deploy.mjs
```

You should run this script after:
- changing the video template
- changing `config.mjs`
- upgrading Remotion to a newer version

### Set up rendering on AWS Lambda

This template supports rendering the videos via [Remotion Lambda](https://remotion.dev/lambda).

1. Copy the `.env.example` file to `.env` and fill in the values.
   Complete the [Lambda setup guide](https://www.remotion.dev/docs/lambda/setup) to get your AWS credentials.

2. Edit the `config.mjs` file to your desired Lambda settings.

3. Run `node deploy.mjs` to deploy your Lambda function and Remotion Bundle.

---

## ⚙️ 技术栈

- Remotion
- Next.js (App Router)
- `@remotion/player`
- `@remotion/lambda`
- Tailwind CSS
- TypeScript
- React