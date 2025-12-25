# Architecture

## Product goal

Deliver stable, DPI-resistant internet connectivity
with minimal user interaction, using Telegram
as the primary entry point.

The product prioritizes reliability and simplicity
over advanced features or optimization.

## User

The primary user is a non-technical person
who wants the internet to “just work”
without understanding VPN protocols or configuration.

## Constraints

- DPI and traffic inspection
- iOS networking restrictions
- Unstable IP environments
- Telegram as the main interaction channel
- Limited operational complexity (solo founder)

## Current checkpoint

This document describes the state of the system
after completing the infrastructure stabilization phase.

## Checkpoint #2 — Telegram bot and subscription architecture

This checkpoint describes how user access, payments, subscriptions,
and VPN configuration delivery are designed before implementation.

The goal is to provide a simple, Telegram-first experience
that minimizes user confusion and operational complexity.

### VPN link generation and delivery

Each user is assigned a unique VPN client
created via the 3x-ui panel API.

The VLESS Reality connection link is generated dynamically
based on the user's client identifier and inbound configuration.

The bot delivers:
- a VLESS connection URI
- an optional QR code for mobile clients

Links are generated on demand and not permanently stored.


---

### Roles

- User — purchases access and connects
- Support — real human operator via Telegram
- Admin — monitoring, manual actions (future)

---

### Core entities

- User: tg_id, username, created_at
- Wallet: tg_id, balance
- Plan: id, name, price, days, traffic_gb (optional), device_limit (optional)
- Invoice: provider, invoice_id, tg_id, amount, status, created_at, paid_at
- Subscription: tg_id, plan_id, active_until, enabled
- VPN Client: tg_id, inbound_id, client_uuid, enabled

Configuration links (VLESS URI) are generated on demand
and are not permanently stored unless required.

---

### Bot main menu (MVP)

- 👤 Personal cabinet
- 🔌 Connect
- 🆘 Support

The interface prioritizes a single primary action ("Connect")
to reduce cognitive load.

---

### Personal cabinet

Displays:
- Wallet balance
- Subscription status (active until / inactive)
- Selected server or country (logical or physical)
- Traffic usage (optional)

Actions:
- Top up balance
- Refresh status
- Back

---

### Connect flow (primary user path)

1. User opens bot and selects "Connect"
2. Bot checks subscription status
3. If subscription is active:
   - Generates or reuses VPN client in 3x-ui
   - Builds VLESS Reality connection URI
   - Sends configuration and short instructions
4. If subscription is inactive:
   - Prompts user to purchase access or top up balance

The system ensures that users can only connect
when their subscription is valid.

---

### Payment flow (wallet-first MVP)

Payments are handled via balance top-up.

Flow:
1. User selects top-up amount
2. Bot creates invoice via payment provider
3. User completes payment externally
4. User presses "I paid"
5. Bot verifies invoice status via API
6. Balance is credited

This approach avoids webhook dependencies
and simplifies early-stage operations.

---

### VPN client provisioning

- Each user receives a unique VPN client
- Client is created via 3x-ui API when needed
- Client identifier is reused for renewals
- Subscription expiration is enforced logically (MVP)

Disabling expired clients at the panel level
may be added in later iterations.

---

### Country / server selection

Two models are supported by design:

- Logical country (marketing / plan-based)
- Physical country (multiple servers)

MVP may start with logical selection
and migrate to physical servers without breaking architecture.

---

### Design principles

- Simplicity over optimization
- Fewer moving parts
- Predictable user flows
- Easy rollback and recovery


