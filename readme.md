# Authentik Managed Identity Service

Reference architecture and tiered service design for SMB identity management, built on Authentik.

## Problem

Small and mid-size businesses need SSO and MFA but don't have the headcount or budget for an enterprise IAM team. Off-the-shelf SaaS identity providers price for enterprise scale and lock customers into vendor-specific extensions they'll never use.

## Architecture

- Authentik running containerized, handling SSO, MFA, and application proxying
- PostgreSQL backing identity data, Redis handling caching and session state
- Cloudflare Tunnel for external access — no open inbound ports
- Each client runs an isolated deployment, not a shared multi-tenant pool — one client's identity data never shares infrastructure with another's

## Service tiers

| Tier | Price | Scope |
|---|---|---|
| Starter | $150–250/mo | Core SSO and MFA, single domain, email support |
| Standard | $350–500/mo | Multi-app SSO, MFA, basic provisioning workflows, priority support |
| Managed | $650–900/mo | Full lifecycle management, custom provisioning, dedicated support, quarterly access reviews |

## Stack

Docker · Authentik · PostgreSQL · Redis · Cloudflare Tunnel

## Outcome

Enterprise-grade SSO and MFA, deployed and supported, at a fraction of enterprise IAM platform cost.

## Notes

This repo documents the reference architecture and service tiers, not a specific client's live deployment. `docker-compose.yml` and `.env.example` use placeholder values — every client deployment is isolated, with its own values, never shared or reused across clients.
