# Audit trails

Patterns for preserving trustworthy evidence of important business actions.

- Record actor, authority context, action, subject, time, reason and result.
- Prefer append-only history over mutable status fields as the only evidence.
- Separate operational history from sensitive payloads and define retention.
- Make the trail useful to operators, reviewers and future investigators.

