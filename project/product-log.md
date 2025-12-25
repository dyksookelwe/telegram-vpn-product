# Product Log

## Checkpoint #1 — Infrastructure stabilization

Date: 22.12.2025

Problem:
VPN setups were complex, unstable, and difficult to maintain.

Hypothesis:
A minimal VLESS + Reality full-tunnel configuration
would provide better stability and DPI resistance.

What was done:
Removed split routing, WARP, and non-essential rules.
Finalized a simple and robust routing model.

Result:
Stable connectivity and successful client connections.

Conclusion:
Simplicity and reliability are more important than optimization.

## Checkpoint #2 — User access & subscription design

Date: 23.12.2025

Problem:
Need a simple Telegram-first UX to sell access, manage subscriptions, and reduce support load.

Hypothesis:
A wallet-based flow + one main “Connect” path + manual payment confirmation ("I paid") will be the simplest MVP without requiring webhooks/domain.

What was done:
Defined entities, menu, user flows, payment flow, and x-ui integration model.

Result:
Documentation baseline ready for implementation.

Conclusion:
Documentation-first reduced ambiguity and prevents rework.

## 3x-ui integration and VLESS link generation

Date: 25.12.2025

Problem:
Needed to generate and deliver a working VLESS Reality link
for each user directly from the Telegram bot.

This turned out to be significantly more complex than expected
due to panel API behavior and configuration constraints.

Hypothesis:
Generating a unique VPN client per Telegram user
and building the VLESS link dynamically
would be the most reliable approach.

What was done:
- Integrated bot with 3x-ui panel API
- Tested multiple approaches to link generation
- Implemented per-user client creation using Telegram ID
- Added optional QR code generation for user convenience

Result:
Users can press "Connect" and receive a working VLESS link.
QR code is available as an optional alternative.

Conclusion:
Panel integrations are often the hardest part of the system.
Simplifying the client model reduced errors and made the system stable.

