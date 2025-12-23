# User Flow (MVP)

## Goal
User connects successfully in ≤ 2 minutes with minimal confusion.

## Primary flow (happy path)
1. User opens bot → /start
2. Sees one main button: "▶️ Connect"
3. Bot checks subscription status:
   - Active → sends config + deep-link + short instructions
   - Not active → offers top-up + plan selection
4. User pays
5. Bot confirms activation and sends config
6. User connects
7. Bot asks: "Connected successfully? ✅/❌"

## Failure flows
### A) App did not open
- Provide alternative: copy link / manual import guide

### B) App opened but did not connect
- Offer "🔁 Repair"
- Offer fallback server/config (later)
- Offer technical support (later)

### C) User confused
- Minimal guide + 1 screenshot + one step at a time
