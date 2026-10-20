---
title: "Remotion Render Server Template"
tags: ["remotion", "template", "server", "render", "express"]
category: "Template"
created: "2026-10-20"
updated: "2026-10-20"
source: "external"
type: "index"
status: "stable"
lifecycle: "active"
---

# Remotion Render Server Template

<p align="center">
  <a href="https://github.com/remotion-dev/logo">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="https://github.com/remotion-dev/logo/raw/main/animated-logo-banner-dark.apng">
      <img alt="Animated Remotion Logo" src="https://github.com/remotion-dev/logo/raw/main/animated-logo-banner-light.gif">
    </picture>
  </a>
</p>

This template provides an Express.js server that allows you to start new video render jobs, track the progress of ongoing renders, and cancel running render jobs.

The server exposes the following main endpoints:

- `POST /renders` - Start a new render job
- `GET /renders/:id` - Get the status of a render
- `DELETE /renders/:id` - Cancel a running render

---

## 💡 概述

A Remotion template that wraps video rendering in an Express.js HTTP server. Enables render job management through a REST API, suitable for integrating Remotion rendering into web services and backend workflows.

---

## ⚡ 功能

- REST API for render job lifecycle management
- Start, track, and cancel render jobs
- Docker support for containerized deployment
- Express.js server with watch mode for development

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

「待补充」

---

## 🚀 快速开始

### Getting Started

**Install Dependencies**

```console
npm install
```

**Start the Render Server**

```console
npm run dev
```

This will start the Express server that handles render requests in watch mode for development.

**Run in Production**

```console
npm start
```

**Run Remotion Studio**

```console
npm run remotion:studio
```

**Render the example video locally**

```
npx remotion render
```

**Upgrade all Remotion packages:**

```
npx remotion upgrade
```

### Docker Support

The template includes Docker support out of the box. Build and run the container using:

```console
docker build -t remotion-render-server .
docker run -d -p 3000:3000 remotion-render-server
```

---

## ⚙️ 技术栈

「待补充」

---

## Docs

Get started with Remotion by reading the [fundamentals page](https://www.remotion.dev/docs/the-fundamentals).

## Help

We provide help on our [Discord server](https://discord.gg/6VzzNDwUwV).

## Issues

Found an issue with Remotion? [File an issue here](https://github.com/remotion-dev/remotion/issues/new).

## License

Note that for some entities a company license is needed. [Read the terms here](https://github.com/remotion-dev/remotion/blob/main/LICENSE.md).