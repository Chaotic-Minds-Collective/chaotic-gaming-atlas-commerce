# CMG Commerce

A Chaotic Minds Gaming-branded multi-grid economy and shop with durable entitlements and reward delivery.

This Chaotic Minds Gaming-specific module extends [Chaotic Gaming Core](https://github.com/Chaotic-Minds-Collective/chaotic-gaming-core) and the [ATLAS integration adapter](https://github.com/Chaotic-Minds-Collective/chaotic-gaming-atlas); it does not replace either foundation.

## Feature scope
- Original CMG shop catalogue and purchase history
- Cluster wallet ledger with idempotent transactions
- Kits, items, services, cosmetics, tame-color tokens and loot boxes
- Vote, playtime, daily, event and community rewards
- VIP entitlements and grid-specific delivery
- Refund/revocation and failed-delivery reconciliation

## Architecture and dependencies
- Core commerce, orders, entitlements, payment integration and reward queue
- ATLAS adapter: player resolution and item grants
- Sentinel for audit; Connect for announcements
- Tribes for optional group rewards

Core remains authoritative for shared identity, authorization and platform records. ATLAS-native calls pass through the shared adapter. This module owns its domain state and must not connect directly to PostgreSQL.

## Implementation plan
See [docs/IMPLEMENTATION_PLAN.md](docs/IMPLEMENTATION_PLAN.md) for data ownership, milestones and technical gates.

## Readiness
Planning scaffold only. Native ATLAS compatibility and feature-specific callbacks are not yet verified on an isolated server. No production deployment is implied.
