# Hyperliquid Trading

Trade perpetual futures, spot, and RWA on Hyperliquid, a fully on-chain decentralized exchange — with market analysis, order management, and wallet-level PnL insight.

## What it is

An agent skill (v1.8.0, script-delivery) for Hyperliquid. Orders are signed with the agent's EVM wallet and submitted directly to the Hyperliquid L1.

**Two lanes:**

- **Read-only queries** — account, balances, PnL history, open orders, orderbook, candles, funding, staking. Works for any wallet address, not just your own.
- **Write operations** — place perp/spot orders, set TP/SL, deposit and withdraw USDC, all through signed scripts.

**32 functions, grouped:** Account (9) · PnL & history (9) · Orders (3) · Market (10) · Staking (3).

## What's inside

- `SKILL.md` — the skill definition, the two-lane model, and function reference
- `scripts/` / `core/` — the script-delivery implementation

## Quick start

```python
from core.skill_tools import hyperliquid

account = hyperliquid.hl_account()
mids    = hyperliquid.hl_market()
candles = hyperliquid.hl_candles(coin="BTC", interval="1h", hours_back=24)
```

Check any wallet's PnL:

```python
hyperliquid.hl_portfolio(address="0x1f16...")   # PnL time series
hyperliquid.hl_account(address="0x1f16...")     # their open positions
```

## Before trading

A wallet policy must be active first. Load the **wallet-policy** skill and set a standard policy (deny key export). Never export or share a private key.

## Risk warning

Trading perpetuals with leverage can lose more than your initial margin. This skill is a tool, not financial advice. Start small, use stops, and never trade money you cannot afford to lose.

## License

MIT — see [LICENSE](LICENSE).
