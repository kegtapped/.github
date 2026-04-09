<div align="center">

<img src="https://kegtapped.com/images/logo-og.png" alt="Keg Tapped" width="280" />

# Keg Tapped

### Discover Your Perfect Beer

**A social beer rating and discovery platform powered by AI flavor profiling, real-time social features, and machine learning recommendations.**

[![Website](https://img.shields.io/badge/kegtapped.com-F59E0B?style=for-the-badge&logo=google-chrome&logoColor=white)](https://kegtapped.com)
[![Discord](https://img.shields.io/badge/Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/GNTMpt2bQ4)
[![Developer Portal](https://img.shields.io/badge/Developer%20API-1e293b?style=for-the-badge&logo=swagger&logoColor=white)](https://developers.kegtapped.com)

---

[![Next.js](https://img.shields.io/badge/Next.js_16-000000?style=flat-square&logo=next.js&logoColor=white)](https://nextjs.org)
[![Go](https://img.shields.io/badge/Go_1.24-00ADD8?style=flat-square&logo=go&logoColor=white)](https://go.dev)
[![Rust](https://img.shields.io/badge/Rust-000000?style=flat-square&logo=rust&logoColor=white)](https://rust-lang.org)
[![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)](https://typescriptlang.org)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL_15-4169E1?style=flat-square&logo=postgresql&logoColor=white)](https://postgresql.org)
[![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)](https://kubernetes.io)
[![Stripe](https://img.shields.io/badge/Stripe-635BFF?style=flat-square&logo=stripe&logoColor=white)](https://stripe.com)

</div>

---

## 🍺 What is Keg Tapped?

Keg Tapped is a next-generation platform for beer enthusiasts, breweries, and craft beer communities. We combine a proprietary **14-question flavor profiling system** with **machine learning recommendations** and **real-time social features** to help you discover beers you'll love — and connect with the people and places behind them.

Whether you're a casual drinker exploring new styles or a brewery owner looking for customer insights, Keg Tapped maps the world of beer, one taste at a time.

---

## ✨ Features

### 🎯 AI-Powered Flavor Profiling

Our proprietary **14-question taste questionnaire** maps every beer and every palate onto a 2D flavor vector — covering hoppy vs. malty, light vs. rich, fruit-forward, roasted, bitterness, sweetness, body, carbonation, and more. Your unique flavor fingerprint drives everything from recommendations to discovery.

### 🤖 Smart Recommendations

A **Rust-powered ML engine** using Alternating Least Squares (ALS) collaborative filtering combined with content-based vector similarity delivers personalized beer suggestions with a taste-match confidence score. Recommendations update daily with sub-millisecond serving latency.

### 🍻 Beer Discovery

Browse and search thousands of beers with advanced filters — style, ABV, IBU, SRM color, brewery, and flavor profile. Sort by rating, popularity, or name. Every beer has a detailed profile with flavor breakdowns, community ratings, and similar beer suggestions.

### 🗺️ Brewery Explorer

An interactive **MapLibre-powered map** for discovering breweries worldwide across 24+ countries. Filter by location, type, and verification status. Brewery owners can **claim and verify** their profiles, manage their beer catalog, and track community engagement.

### 💬 Real-Time Social

A full social network built for beer — follow friends and breweries, post tastings, comment, like, and direct message. Powered by **WebSocket infrastructure** with typing indicators, read receipts, and presence tracking.

### ⭐ Ratings & Reviews

Rate beers across multiple dimensions with written reviews and flavor questionnaire answers. Community ratings use **Bayesian averaging** and **Wilson score confidence intervals** for fair, statistically sound rankings — even for beers with few reviews.

### 🏆 Badges & Gamification

Earn achievement badges like *First Review*, *Beer Enthusiast* (50 ratings), *Taste Explorer* (15 styles), and *Social Butterfly*. Track your points, level up, and build your beer reputation.

### 📱 Progressive Web App

Installable on any device with offline support, home screen shortcuts (Scan Beer, Nearby Breweries, New Rating), and native share target integration. Works everywhere — no app store required.

---

## 🏗️ Architecture

Keg Tapped is a **polyglot microservices platform** — five services, three languages, self-hosted on bare-metal Kubernetes.

```
┌─────────────────────────────────────────────────────────────┐
│                      Frontend                                │
│     Next.js 16  •  TypeScript  •  React  •  TailwindCSS     │
│       App Router  •  Server Components  •  PWA               │
└──────────────────────────┬──────────────────────────────────┘
                           ▼
┌──────────────────────────────────────────────────────────────┐
│                    API  &  Services                           │
│                                                              │
│   ┌──────────┐   ┌──────────┐   ┌──────────┐   ┌────────┐  │
│   │  Go API  │   │ WebSocket│   │  Worker  │   │ ML Rust│  │
│   │ chi/v5   │   │ Gorilla  │   │  Images  │   │ gRPC   │  │
│   │ REST     │   │ Real-time│   │ Indexing │   │ ALS    │  │
│   └──────────┘   └──────────┘   └──────────┘   └────────┘  │
└──────────────────────────┬──────────────────────────────────┘
                           ▼
┌──────────────────────────────────────────────────────────────┐
│                    Infrastructure                             │
│   PostgreSQL 15  •  Redis  •  Talos Linux K8s  •  Traefik   │
│   cert-manager  •  ArgoCD  •  NAS Storage  •  Self-hosted   │
└──────────────────────────────────────────────────────────────┘
```

| Service | Language | Purpose |
|---------|----------|---------|
| **web** | TypeScript / Next.js 16 | SSR frontend, BFF proxy, PWA |
| **api-go** | Go 1.24 / chi | REST API, business logic, Stripe billing |
| **ws** | Go / Gorilla | Real-time messaging, presence, notifications |
| **worker-images** | Go | Background image indexing and optimization |
| **ml-rust** | Rust / Tonic gRPC | ALS recommendation engine, vector similarity |

### Infrastructure

- **Kubernetes** on Talos Linux — immutable OS, self-hosted bare-metal cluster
- **Traefik** ingress with automatic TLS via Let's Encrypt
- **PostgreSQL 15** as a StatefulSet with NAS-backed persistent storage
- **Redis 7** for caching, sessions, and pub/sub
- **ArgoCD** for GitOps-driven deployments
- **GitHub Actions** CI/CD with lint, typecheck, test, build, security scan, and auto-deploy
- **Zero cloud vendor lock-in** — fully on-premises, no managed cloud services

---

## 📊 By the Numbers

<div align="center">

| | | | |
|:---:|:---:|:---:|:---:|
| **117,000+** | **5** | **35+** | **3** |
| Lines of Code | Microservices | API Endpoints | Languages |

</div>

---

## 💼 Plans & Pricing

| | Free | Starter | Growth | Enterprise |
|---|:---:|:---:|:---:|:---:|
| **Price** | $0/mo | $29/mo | $79/mo | Custom |
| Rate & review beers | ✅ | ✅ | ✅ | ✅ |
| Flavor profiling & recommendations | ✅ | ✅ | ✅ | ✅ |
| Social features | ✅ | ✅ | ✅ | ✅ |
| List your beers | — | Up to 10 | Up to 100 | Unlimited |
| Analytics | — | Basic | Advanced | Custom |
| Verified badge | — | — | ✅ | ✅ |
| Ad-free experience | — | Reduced | ✅ | ✅ |
| API access | — | — | — | ✅ |
| Dedicated support & SLA | — | — | — | ✅ |

---

## 🔌 Developer API

Businesses with a Keg Tapped subscription can access our API for integrating beer data, ratings, recommendations, and brewery information into their own applications.

**→ [developers.kegtapped.com](https://developers.kegtapped.com)**

---

## 👥 Team

| Name | Role |
|------|------|
| **Joshua Baney** | CEO & Founder |
| **Dalton Nelson** | COO & Business Advisor |
| **Patrick Nelson** | CFO |
| **AJ** | SVP of Product Alignment & Success |
| **Jacob Baney** | SVP of Business Development |
| **Will Syme** | VP of Sales & Marketing |

---

## 📬 Contact

| Email | Department |
|-------|------------|
| [hello@kegtapped.com](mailto:hello@kegtapped.com) | General Inquiries |
| [sales@kegtapped.com](mailto:sales@kegtapped.com) | Sales Team |
| [engineering@kegtapped.com](mailto:engineering@kegtapped.com) | General Software Development |
| [platform@kegtapped.com](mailto:platform@kegtapped.com) | Platform Engineering |
| [devops@kegtapped.com](mailto:devops@kegtapped.com) | DevOps Engineering |
| [security@kegtapped.com](mailto:security@kegtapped.com) | Security Concerns & Bounties |
| [new-brew@kegtapped.com](mailto:new-brew@kegtapped.com) | New Brewery Verification |
| [data@kegtapped.com](mailto:data@kegtapped.com) | Data Compliance |
| [legal@kegtapped.com](mailto:legal@kegtapped.com) | Legal Inquiries |
| [compliance@kegtapped.com](mailto:compliance@kegtapped.com) | Government & Regulatory |
| [abuse@kegtapped.com](mailto:abuse@kegtapped.com) | Abuse Reports |

---

## 🌐 Connect

<div align="center">

[![Discord](https://img.shields.io/badge/Discord-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/GNTMpt2bQ4)
[![Twitter](https://img.shields.io/badge/@kegtapped-1DA1F2?style=for-the-badge&logo=twitter&logoColor=white)](https://twitter.com/kegtapped)
[![Instagram](https://img.shields.io/badge/@kegtapped-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://instagram.com/kegtapped)
[![LinkedIn](https://img.shields.io/badge/Keg_Tapped-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/company/108941286)
[![Facebook](https://img.shields.io/badge/Keg_Tapped-1877F2?style=for-the-badge&logo=facebook&logoColor=white)](https://facebook.com/profile.php?id=61580707470847)

</div>

---

## 📄 Legal

- [Terms of Service](https://kegtapped.com/legal/terms-of-service)
- [Privacy Policy](https://kegtapped.com/legal/privacy-policy)
- [Data Deletion](https://kegtapped.com/legal/data-deletion)
- [COPPA Compliance](https://kegtapped.com/legal/coppa)
- [Age Requirement & Alcohol Responsibility](https://kegtapped.com/legal/age-disclosure)
- [IP & DMCA](https://kegtapped.com/legal/ip-dmca)

---

<div align="center">

**© 2025 Keg Tapped. All rights reserved.**

Made with 🍺 by beer lovers.

</div>
