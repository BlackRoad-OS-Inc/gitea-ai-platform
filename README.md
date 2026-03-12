# Gitea AI Platform

[![CI](https://github.com/blackboxprogramming/gitea-ai-platform/actions/workflows/ci.yml/badge.svg)](https://github.com/blackboxprogramming/gitea-ai-platform/actions/workflows/ci.yml)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6.svg)](https://typescriptlang.org)
[![Cloudflare Workers](https://img.shields.io/badge/Cloudflare-Workers-F38020.svg)](https://workers.cloudflare.com)
[![Claude AI](https://img.shields.io/badge/Claude-code_review-CC785C.svg)](https://anthropic.com)
[![Gitea](https://img.shields.io/badge/Gitea-self--hosted-609926.svg)](https://gitea.io)

> **AI-powered Gitea automation on Cloudflare Workers** — Claude-powered PR code review, AI issue triage, auto-deploy webhooks, GitHub↔Gitea mirroring, and real-time dashboard.

## Features

- **AI Code Review** — Claude analyzes PRs for bugs, security issues, and style violations
- **Issue Triage** — Automatic priority and label assignment using AI classification
- **Auto Deploy** — Webhook-triggered deployments to Cloudflare Pages on push
- **GitHub Mirror** — Bi-directional sync between Gitea and GitHub repositories
- **Dashboard API** — Real-time deployment logs, repo stats, and activity feed

## Architecture

```
Gitea → Webhook → Cloudflare Worker → Claude API → PR Comment
                                     → Cloudflare Pages Deploy
                                     → GitHub Mirror Sync
```

## Endpoints

| Route | Method | Description |
|-------|--------|-------------|
| `/webhook/push` | POST | Handle push events, trigger deploys |
| `/webhook/pr` | POST | AI code review on pull requests |
| `/webhook/issue` | POST | AI issue triage and labeling |
| `/api/chat` | POST | Chat with AI about your codebase |
| `/api/mirror` | POST | Sync repo to GitHub |
| `/api/repos` | GET | List all repositories |
| `/api/deploys` | GET | Recent deployment logs |
| `/dashboard` | GET | Real-time dashboard UI |

## Deploy

```bash
cd worker
npm install
npx wrangler deploy
```

## Tech Stack

- **Runtime**: Cloudflare Workers (edge, globally distributed)
- **Language**: TypeScript
- **AI**: Anthropic Claude API with Workers AI fallback
- **Storage**: Cloudflare KV for deploy logs
- **Git**: Gitea API + GitHub API

## License

Proprietary — BlackRoad OS, Inc.
