# Technical Decision Guide for Non-Developer Audience

## Purpose

This workshop targets non-developers (product owners, business analysts, designers, managers). When making any technical decision, present three deployment tiers so participants can choose based on their real-world context. The goal is to demystify technical choices and empower non-technical stakeholders to make informed decisions.

## When to Apply

Present the three-tier options table whenever a decision involves:

- **Infrastructure**: compute, storage, networking, CDN, DNS
- **Database**: data storage engine, caching layer, search index
- **Authentication & Security**: identity provider, API keys, OAuth, encryption
- **Deployment**: hosting, CI/CD pipeline, containerization, domain setup
- **Architecture**: monolith vs. microservices, serverless vs. traditional, event-driven patterns
- **Tooling**: frameworks, languages, package managers, monitoring
- **Integration**: third-party APIs, messaging queues, notification services
- **Cost & Scaling**: pricing model, auto-scaling strategy, resource limits

## Tier Definitions

| Tier | Intent | Typical Audience | Lifespan |
|------|--------|------------------|----------|
| 🟢 **POC** (Proof of Concept) | Validate an idea as fast as possible with minimal setup | Hackathons, demos, solo experimentation | Hours to days |
| 🟡 **Dev** (Development) | Build and test with a small team; acceptable for internal use | Pilots, internal tools, staging environments | Weeks to months |
| 🔴 **Production** | Serve real users with reliability, security, and scalability | Customer-facing services, revenue-generating products | Months to years |

## Presentation Format

For every technical decision point, present a table with the following columns:

| Tier | Option | What It Does | Cost | Setup Time | Upgrade Path |
|------|--------|--------------|------|------------|--------------|
| 🟢 POC | (simplest option) | One-sentence plain-language explanation | Free / minimal | Minutes | How to move to Dev |
| 🟡 Dev | (balanced option) | One-sentence plain-language explanation | Low / free-tier eligible | Hours | How to move to Production |
| 🔴 Production | (enterprise-grade option) | One-sentence plain-language explanation | Paid / usage-based | Days | Already at target state |

After the table, always include:

1. **Recommendation** — Which tier to use for this workshop (default: POC) and why.
2. **Key Trade-off** — One sentence explaining what you gain and what you give up at the recommended tier.
3. **Upgrade Note** — Whether migrating to a higher tier later requires rework or is a configuration change.

## Rules

1. **Default to POC** — Always recommend POC unless there is a specific reason not to (e.g., the feature only exists at a higher tier).
2. **Plain language only** — Every technical term must include a parenthetical explanation on first use. Example: "RDS (a managed database service that handles backups and updates for you)".
3. **Show cost impact** — Use simple labels: Free, Free Tier (limited), Low cost (~$X/month), or Paid (estimate range).
4. **Show time-to-working** — Indicate how long it takes to get the option running: minutes, hours, or days.
5. **Clarify reversibility** — Explicitly state whether the choice is easy to change later or locks you in.
6. **One pro, one con** — For each option, state the single biggest advantage and the single biggest limitation.
7. **No jargon without context** — Assume the reader has never used a terminal. If a concept requires background knowledge, provide it inline.
8. **Group related decisions** — If two decisions are tightly coupled (e.g., database + ORM), present them together with a note on how they interact.

## Examples

### Example 1: Database Selection

| Tier | Option | What It Does | Cost | Setup Time | Upgrade Path |
|------|--------|--------------|------|------------|--------------|
| 🟢 POC | SQLite (file-based database) | Stores data in a single file alongside your app. No server needed. | Free | 1 minute | Export data and import into RDS |
| 🟡 Dev | Amazon RDS for PostgreSQL (managed database) | A database server that AWS manages — handles backups, patches, and restarts for you. | Free Tier eligible (~$0 for 12 months) | 30 minutes | Change instance size and enable Multi-AZ |
| 🔴 Production | Amazon Aurora (high-performance managed database) | Auto-scales reads, replicates across zones, handles millions of requests. | ~$50-200/month depending on usage | 1-2 hours | Already production-grade |

> **Recommendation**: Use 🟢 SQLite for this workshop. It requires zero configuration and lets you focus on the application logic.
>
> **Key Trade-off**: You get instant setup, but only one person can write to the database at a time.
>
> **Upgrade Note**: Migration to RDS/Aurora later requires exporting your data and updating one configuration file — straightforward, no code rewrite needed.

### Example 2: Deployment Strategy

| Tier | Option | What It Does | Cost | Setup Time | Upgrade Path |
|------|--------|--------------|------|------------|--------------|
| 🟢 POC | Local development server | Run the app on your own machine. Access it at `localhost`. | Free | Instant | Deploy to App Runner with one command |
| 🟡 Dev | AWS App Runner (managed container hosting) | Upload your code, AWS runs it and gives you a public URL. No server management. | ~$5-15/month | 15 minutes | Add custom domain and auto-scaling rules |
| 🔴 Production | Amazon ECS on Fargate (container orchestration) | Run multiple copies of your app with load balancing, auto-scaling, and health checks. | ~$30-100+/month | 2-4 hours | Already production-grade |

> **Recommendation**: Use 🟢 local development server for this workshop. You'll see results immediately without any cloud setup.
>
> **Key Trade-off**: You get zero cost and instant feedback, but only you can access the app (no public URL).
>
> **Upgrade Note**: The same code runs in all three tiers without modification. Moving up only changes where and how the app is hosted.

### Example 3: Authentication

| Tier | Option | What It Does | Cost | Setup Time | Upgrade Path |
|------|--------|--------------|------|------------|--------------|
| 🟢 POC | Hardcoded test users | A few fake users built into the code for testing. No login page needed. | Free | 5 minutes | Replace with Cognito user pool |
| 🟡 Dev | Amazon Cognito (managed auth service) | Provides sign-up, sign-in, and password reset out of the box. | Free up to 50,000 users/month | 1 hour | Enable MFA and advanced security |
| 🔴 Production | Cognito + WAF + MFA (full security stack) | Multi-factor authentication, brute-force protection, compliance-ready. | ~$10-50/month + WAF costs | 3-5 hours | Already production-grade |

> **Recommendation**: Use 🟢 hardcoded test users for this workshop. It eliminates auth complexity so you can focus on building features.
>
> **Key Trade-off**: You skip login entirely (faster iteration), but there's no real security — fine for a workshop, not for real users.
>
> **Upgrade Note**: Adding Cognito later requires adding a login page and wrapping API calls with token validation — moderate effort, but well-documented.
