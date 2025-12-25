# Key Decisions

## Full tunnel instead of split routing

Date: 22.12.2025

Context:
Split routing adds complexity and increases failure points.

Options considered:
- Split routing by geo/domain
- Full tunnel through VPS

Decision:
Use full tunnel routing for all user traffic.

Reason:
Maximize reliability and minimize configuration errors.

Risks:
Higher load on the VPS.

## Decision: Wallet-first payment model

Date: 23.12.2025

Context:
Need flexible renewals, refunds, and manual adjustments.

Options:
- Direct tariff purchase
- Wallet balance with deduction

Decision:
Use wallet-first model.

Why:
Simplifies renewals, discounts, and compensation.

Risks:
Additional balance state to manage.

## Decision: Manual payment confirmation ("I paid")

Date: 23.12.2025

Context:
Early MVP without public webhooks or complex domain setup.

Options:
- Automatic webhooks
- Manual confirmation with invoice status check

Decision:
Use "I paid" confirmation button.

Why:
Reduces infrastructure complexity at early stage.

Risks:
User may forget to confirm payment.

## Decision: Single primary "Connect" action

Date: 23.12.2025

Context:
Users are non-technical and fear breaking configurations.

Options:
- Multiple visible modes and settings
- One primary action with hidden complexity

Decision:
Expose one main "Connect" path.

Why:
Reduces confusion and support requests.

Risks:
Advanced users may want more control.

## Decision: One VPN client per Telegram user

Date: 25.12.2025

Context:
Generating VLESS Reality links through 3x-ui API
proved unreliable with shared or reused configurations.

Options:
- Reuse a shared client or static config
- Generate a new client per user

Decision:
Create a unique VPN client per Telegram user
and bind it to the user's Telegram ID.

Why:
Improves reliability, simplifies troubleshooting,
and avoids cross-user conflicts.

Risks:
Higher number of clients in the panel.

## Decision: QR code as optional connection method

Date: 25.12.2025

Context:
Some users struggle with copying and importing VLESS links,
especially on mobile devices.

Options:
- Text link only
- QR code only
- Text link + optional QR code

Decision:
Provide QR code as an optional connection method.

Why:
Improves usability without forcing a new flow.
Keeps primary path simple.

Risks:
May be unused or unnecessary (to be validated).

