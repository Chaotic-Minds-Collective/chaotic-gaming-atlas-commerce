# CMG Commerce — Implementation Plan

## Purpose
A Chaotic Minds Gaming-branded multi-grid economy and shop with durable entitlements and reward delivery.

## Feature scope
- Original CMG shop catalogue and purchase history
- Cluster wallet ledger with idempotent transactions
- Kits, items, services, cosmetics, tame-color tokens and loot boxes
- Vote, playtime, daily, event and community rewards
- VIP entitlements and grid-specific delivery
- Refund/revocation and failed-delivery reconciliation

## Dependencies
- Core commerce, orders, entitlements, payment integration and reward queue
- ATLAS adapter: player resolution and item grants
- Sentinel for audit; Connect for announcements
- Tribes for optional group rewards

## Data ownership
Core owns wallet, orders, payments, entitlements and reward jobs. Commerce owns ATLAS item IDs, bundles, loot-box tables and delivery mappings.

## Milestones
1. Map Core commerce APIs and verify schemas
2. Define ATLAS item IDs and delivery contract
3. Build read-only catalogue and wallet display
4. Use Core orders/entitlements, no independent payment processing
5. Build leased reward worker; acknowledge only after confirmed game grant
6. Add reward sources, loot boxes and reconciliation

## Technical gates and risks
- Actual ATLAS item delivery is not yet proven
- No live payment keys or production checkout; test mode only
- Publish loot-box odds and audit RNG

## Shared engineering requirements
- Use authenticated, least-privilege Core APIs; no direct database credentials in plugins.
- Preserve provider identifiers as strings; display names are not identifiers.
- Carry cluster, grid and server context on applicable records/events.
- Use stable event IDs, idempotency keys and correlation IDs.
- Keep network work off game-critical threads; use bounded timeouts, retries and circuit breakers.
- Keep secrets out of source control and separate credentials per server/integration.
- Add unit tests, fake-adapter contract tests and isolated runtime compatibility tests.
- Gate unsupported features behind explicit capabilities; fail closed for privileged actions.
- Do not deploy to production or change live server configuration during repository planning.

## Current readiness
Documentation and planning scaffold. Exact ATLAS server build, loader, SDK, callbacks and feature-specific capabilities require isolated reproducible validation.
