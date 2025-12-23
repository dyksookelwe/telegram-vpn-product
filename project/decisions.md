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
