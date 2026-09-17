# ModelWise — AI Governance Boundary Patch

Status: IMPLEMENTED / NOT YET VERIFIED.

Adds deterministic pre-provider governance admission checks to the Model Gateway: kill switch, tenant enablement, model allowlist, input/output limits, request-rate limit contract, and monthly token-budget admission.

Important: this patch intentionally does **not** claim production rate limiting or budget enforcement. The current gateway uses a zeroed usage snapshot as a development-safe boundary. Production must load durable tenant policy and usage counters from PostgreSQL/Redis (or equivalent) under authenticated tenant context, then record the resulting decision and usage in `AiInteraction`.

AI remains advisory. It cannot determine regulated competency pass/fail.
