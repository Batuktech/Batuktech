<p align="center">
  <a href="https://portfolio.batuukka.com"><img src="https://portfolio.batuukka.com/opengraph-image" width="760" alt="Batzorig Arslan, full-stack developer and DevOps engineer at erxes, Ulaanbaatar, Mongolia. Opens portfolio.batuukka.com"></a>
</p>

# Batzorig Arslan

Full-stack developer and DevOps engineer at [erxes](https://erxes.io), based in Ulaanbaatar, Mongolia. I build product interfaces and the systems behind them: APIs, data, and the platforms they run on. At work that means CMS features, plugin access driven by Stripe billing, custom domains for help centers and sites, and the release pipeline that ships them. I also build [Cutroom](https://github.com/Batuktech/Cutroom), a local-first video clipping studio whose clip-scoring commit was selected for the XERJ Corpus Hub.

[![Portfolio](https://img.shields.io/badge/portfolio-portfolio.batuukka.com-2146f5?style=flat)](https://portfolio.batuukka.com)
[![Email](https://img.shields.io/badge/email-batuukka%40gmail.com-2146f5?style=flat)](mailto:batuukka@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Batzorig%20Arslan-2146f5?style=flat)](https://www.linkedin.com/in/batzorig-arslan-11393b32b/)

## 01 / Now at erxes

My product work lands in the public [erxes/erxes](https://github.com/erxes/erxes) repo, so each area below links to merged PRs you can read.

[![erxes stars](https://img.shields.io/github/stars/erxes/erxes?style=flat&logo=github&label=erxes)](https://github.com/erxes/erxes)
[![merged PRs in erxes/erxes](https://img.shields.io/github/issues-search?query=repo%3Aerxes%2Ferxes%20is%3Apr%20author%3ABatuktech%20is%3Amerged&label=merged%20PRs%20in%20erxes%2Ferxes&color=2146f5)](https://github.com/erxes/erxes/pulls?q=is%3Apr+author%3ABatuktech+is%3Amerged)

**Latest merged, October 2026:** [#9880](https://github.com/erxes/erxes/pull/9880) CMS page edits save again and each CMS card opens its own record · [#9793](https://github.com/erxes/erxes/pull/9793) Company Brain runs as a normal plugin on v2 workspaces · [#9679](https://github.com/erxes/erxes/pull/9679) social-post deliveries run on demand per tenant instead of a polling sweep across all tenants

- **Content (CMS) plugin.** Headless client-portal GraphQL APIs, multilingual posts, pages, categories and menus, CMS permissions, a Knowledge Base-to-CMS importer that dry-runs by default and resumes after a crash, and permission-checked sharing of CMS posts to social channels.<br>PRs: [#7544](https://github.com/erxes/erxes/pull/7544) · [#7536](https://github.com/erxes/erxes/pull/7536) · [#7687](https://github.com/erxes/erxes/pull/7687) · [#9271](https://github.com/erxes/erxes/pull/9271) · [#9329](https://github.com/erxes/erxes/pull/9329)
- **Custom domains on erxes Cloud.** Help centers on a workspace's own domain through Cloudflare for SaaS custom hostnames with automatic certificates, later one domain per help center. Web-builder sites connect their own domains through Vercel's domains API, on top of the web builder's Vercel deployment backend.<br>PRs: [#9468](https://github.com/erxes/erxes/pull/9468) · [#9567](https://github.com/erxes/erxes/pull/9567) · [#7104](https://github.com/erxes/erxes/pull/7104)
- **Plugin access from billing.** Plugins for workspaces created on dashboard.erxes.io come from their Stripe subscriptions, bundles and free plans, cached in Redis with a 24-hour last-known-good copy so a short Stripe outage doesn't empty a workspace. Existing workspaces keep their current path. Also shared plan-limit helpers for AI-assistant quotas.<br>PRs: [#9741](https://github.com/erxes/erxes/pull/9741) · [#8503](https://github.com/erxes/erxes/pull/8503)
- **Platform and automation.** Per-pipeline property selection for Sales deals and Frontline tickets with no migration, configurable access-token lifetimes for confidential OAuth clients, and a GitHub Actions workflow that turns Sentry issues into draft fix PRs with an AI coding agent.<br>PRs: [#9001](https://github.com/erxes/erxes/pull/9001) · [#7846](https://github.com/erxes/erxes/pull/7846) · [#7812](https://github.com/erxes/erxes/pull/7812) · [#7837](https://github.com/erxes/erxes/pull/7837)

The delivery side lives in private repos, so it gets a description and no links. Right now I'm cutting erxes.io over to a new customer account and billing service, data migration included. Alongside that: release CI that publishes plugin UIs in parallel, versioned SaaS rollouts managed as code with GitOps, and maintenance and backup tooling for enterprise installs.

## 02 / Open source

### [Cutroom](https://github.com/Batuktech/Cutroom)

[![XERJ Corpus Hub contributor](https://hub.xerj.org/contributors/Batuktech/badge.svg)](https://hub.xerj.org/contributors/Batuktech)
[![Cutroom stars](https://img.shields.io/github/stars/Batuktech/Cutroom?style=flat)](https://github.com/Batuktech/Cutroom)
[![License](https://img.shields.io/github/license/Batuktech/Cutroom)](https://github.com/Batuktech/Cutroom/blob/main/LICENSE)
[![CI](https://github.com/Batuktech/Cutroom/actions/workflows/ci.yml/badge.svg)](https://github.com/Batuktech/Cutroom/actions/workflows/ci.yml)

**Turn long recordings into captioned clips on your own computer.** Cutroom transcribes with faster-whisper, has local Qwen3-8B or a bring-your-own-key cloud model propose highlights, styles animated captions, and exports MP4 and SRT through FFmpeg. No account, subscription or paid API required.

<p align="center"><a href="https://github.com/Batuktech/Cutroom"><img src="https://raw.githubusercontent.com/Batuktech/Cutroom/main/docs/assets/editor.png" width="720" alt="Cutroom editor on a sample project: a 16:9 clip preview with a burned-in caption, the timestamped transcript in the right panel, and a waveform timeline with in and out points"></a><br><sub>Fig. 01 / Cutroom editor, sample project</sub></p>

- **Scores that cite the transcript.** In [PR #9](https://github.com/Batuktech/Cutroom/pull/9) I added one versioned rubric (hook, payoff, clarity, novelty, emotion, value) shared by local and cloud review. The model returns transcript segment indexes and Cutroom copies the quotes and timings itself, so a score can't cite a line nobody said. The TypeScript and Python implementations share fixtures and regression tests. The scores are editorial heuristics, not predictions of views.
- **In the XERJ Corpus Hub.** That commit, [`f168f6dc2c`](https://github.com/Batuktech/Cutroom/commit/f168f6dc2c1104fb685e2bb45a1256c364cf98e1), was selected for the [XERJ Corpus Hub](https://hub.xerj.org/contributors/Batuktech), a reference corpus AI coding agents search for worked examples. The corpus is in license review.
- **Stream autopilot.** Paste a finished YouTube VOD and Cutroom splits it into one-hour parts, transcribes each with Whisper large-v3, lets local Qwen pick the strongest moments, ranks them across the whole stream, and renders the top clips at 9:16.
- **How it's built.** A React 19 + Vite UI, an Express 5 API bound to 127.0.0.1 with one cancellable processing queue, Python workers (faster-whisper, OpenCV, yt-dlp, llama-cpp-python on Vulkan), and TypeScript contracts in `shared/` used by both preview and render. CI runs on Node 22 and 24 and renders real captions with FFmpeg.
- **Limits, stated up front.** Pre-1.0, source only, tested on Ubuntu/Linux. Local Qwen needs Linux, an NVIDIA GPU and Vulkan; Whisper runs on CPU. Read the [architecture](https://github.com/Batuktech/Cutroom/blob/main/docs/architecture.md) and [AI scoring](https://github.com/Batuktech/Cutroom/blob/main/docs/ai-suggestions.md) docs.

### Also public

- [Batuktech-Agent](https://github.com/Batuktech/Batuktech-Agent): a one-command installer for a 44-skill pack for AI coding agents such as Codex, Claude Code and Cursor. It bundles 28 curated OpenAI skills, 6 Composio skills and 10 of my own for design, frontend, backend, GraphQL, databases, microservices, DevOps, debugging, security and Git.
- [dayan-mining](https://github.com/Batuktech/dayan-mining): a Mongolian/English site for Dayan Contract Mining on Next.js 16, React 19 and next-intl, with services, projects and news pulled from the erxes CMS over GraphQL.
- [hackathonthesis](https://github.com/Batuktech/hackathonthesis): Thesis Orchestral Defense, a one-day team hackathon build with [@Ireedui0223](https://github.com/Ireedui0223) for running university thesis defenses, with dashboards for admins, teachers and students. Next.js, Fastify, Prisma and PostgreSQL, with a Docker Compose, Nginx and Certbot setup for a Hetzner VPS.

## 03 / Systems

All four are private work, so each name links to a write-up on my portfolio instead of a repo.

| Detail | System | What it does | Built with |
| :-: | :-- | :-- | :-- |
| A | [AI Assistant Gateway](https://portfolio.batuukka.com/work/ai-assistant-gateway) | One multi-tenant gateway routes Discord interactions to isolated customer assistant runtimes | TypeScript, Node.js, Discord, Docker, OpenClaw |
| B | [Enterprise Kubernetes](https://portfolio.batuukka.com/work/enterprise-kubernetes) | Multi-tenant enterprise platform on Hetzner, managed as code with Talos, Terraform and GitOps | Kubernetes, Talos, Terraform, Argo CD, Traefik |
| C | [Legacy CMS migration](https://portfolio.batuukka.com/work/legacy-cms-migration) | A 14 GB archive moved to object storage with validation; 21,306 asset references processed | Node.js, Python, MySQL, Cloudflare R2, JSONL |
| D | [Managed AI runtimes](https://portfolio.batuukka.com/work/managed-ai-runtimes) | Automated OpenClaw provisioning that streams deployment payloads past Linux argument-size limits | Docker, GitHub Actions, OpenClaw, Linux |

## 04 / Websites and products

| No. | Work | Scope | See it |
| :-- | :-- | :-- | :-- |
| W/01 | Tegri Gobi Resort | Accommodation, activities, multilingual stories and booking journeys in one site | [case study](https://portfolio.batuukka.com/work/tegri-gobi-resort) · [tegrigobiresort.com](https://www.tegrigobiresort.com/) |
| W/02 | APU Dairy | Product catalog, recipes, sustainability stories and company news in one brand site | [case study](https://portfolio.batuukka.com/work/apu-dairy) · [apudairy.mn](https://www.apudairy.mn/) |
| W/03 | Geological Society of Mongolia | Mongolian-first platform for membership, news, events, publications and professional resources | [case study](https://portfolio.batuukka.com/work/geological-society-of-mongolia) · [preview](https://geo-society.vercel.app/) |
| W/04 | Erxes XOS | Customer-facing flows, plugin interfaces, GraphQL services and production delivery across erxes | [case study](https://portfolio.batuukka.com/work/erxes-xos) · [erxes.io](https://erxes.io) |
| W/05 | Frontline & Knowledge Base | Ported the erxes 2.0 Knowledge Base into the Frontline plugin for erxes 3.0 | [case study](https://portfolio.batuukka.com/work/frontline-knowledge-base) · [#6808](https://github.com/erxes/erxes/pull/6808) |

## 05 / Stack

| Layer | What I use |
| :-- | :-- |
| 01 Interface | TypeScript, React, Next.js (App Router), Tailwind CSS, Apollo Client, next-intl, GSAP, Framer Motion |
| 02 API | Node.js, GraphQL, Apollo, Express, Fastify, Zod, Stripe |
| 03 Data | MongoDB, Redis, PostgreSQL (Prisma), MySQL, Cloudflare R2 |
| 04 Infrastructure | Docker, Kubernetes on Talos, Terraform, Argo CD, Traefik, GitHub Actions, Hetzner, Cloudflare, Vercel, Nginx |
| AI and media | faster-whisper, Qwen via llama-cpp-python, FFmpeg, OpenClaw |

<sub>Coursework: Spring Boot, Flutter with Firebase, Kotlin.</sub>

## 06 / Contact

For questions about erxes, Cutroom or anything above, email me or reach out on LinkedIn.

[batuukka@gmail.com](mailto:batuukka@gmail.com) · [portfolio.batuukka.com](https://portfolio.batuukka.com) · [LinkedIn](https://www.linkedin.com/in/batzorig-arslan-11393b32b/)

<p align="right"><sub>Drawn in Ulaanbaatar · Rev. 2026</sub></p>
