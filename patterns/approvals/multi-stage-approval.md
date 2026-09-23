# Multi-stage approval

## Problem

An approval is rarely a boolean. The decision may depend on amount, risk, role, evidence, separation of duties, delegation, deadlines and the ability to explain later who decided what and why.

Treating it as `approved: true` hides the process and makes change, audit and recovery difficult.

## When to use it

Use this pattern when a business decision has two or more meaningful stages, different authorities, material evidence, or a requirement to resume and explain the decision later.

## When not to use it

Do not create a workflow for a low-risk confirmation that has no distinct authority or audit requirement. A simple validated action may be enough.

## Model

Represent an approval as an explicit process with:

- a subject and business context;
- a current stage and overall status;
- a policy or rule version;
- required evidence;
- assigned authority and delegation context;
- decisions, reasons and timestamps;
- deadlines, escalation and exception state;
- an immutable history of transitions.

The approval policy should determine the route. A person should decide within a defined authority boundary; the system should record the decision and enforce the consequences.

## Invariants

- A person cannot approve their own conflicting action when separation of duties applies.
- A decision is never silently replaced; corrections are new events or explicit reversals.
- Reopening an approval requires a reason and a new policy evaluation.
- The process can be resumed after a timeout or system failure without losing the decision history.

## Implementation considerations

Keep business state separate from notifications and interface state. Store the policy version used for each approval. Make transitions explicit and idempotent. Treat evidence as part of the decision record, with access controls and retention appropriate to its sensitivity.

Deadlines should be modeled as business behavior, not only as background jobs. The system needs a clear rule for reassignment, escalation, expiry and delegation.

## Failure modes

- A notification is sent twice and creates duplicate decisions.
- A policy changes while an approval is in progress and the system cannot explain which rule applied.
- A delegated approver acts outside the intended scope.
- A failed integration advances the visible status without durable evidence.
- An administrator edits history instead of recording a correction.

## Example

A purchase above a threshold requires a budget owner, then a risk reviewer. The second stage cannot be assigned to the person who created the purchase. If the budget owner does not act by the deadline, the process escalates to a named delegate. Every decision records the authority, evidence, rule version and reason.

