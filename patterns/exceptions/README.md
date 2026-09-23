# Exceptions

Patterns for operational cases that do not follow the normal path and must remain visible, owned and recoverable.

- Exception records should have an owner, reason, severity, next action and deadline.
- The normal workflow should not be polluted with undocumented special cases.
- Resolution should preserve what happened and why the normal rule did not apply.

