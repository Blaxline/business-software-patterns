# Idempotency

Patterns for making retries safe when commands, messages or external callbacks may arrive more than once.

- Give each business operation a stable idempotency key.
- Persist the outcome needed to answer a repeated request consistently.
- Distinguish a duplicate from a new operation with the same payload.
- Define the scope and retention of keys according to business risk.

