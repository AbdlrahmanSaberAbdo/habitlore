# Review Comments are not Corrections, and count only when Upheld

A reviewer's comment on a Pull Request is the same kind of signal as a Correction, but habitlore keeps it as its own term, the Review Comment, rather than widening Correction. Correction stays a User Message to an agent, so Corrections per Task and the Pilot's Verdicts keep measuring agents alone. A Review Comment only becomes Evidence once it is Upheld: the author changed the code or agreed. Received Upheld Review Comments join the same Correction Clusters as Corrections and so produce Rules. Comments the person writes on other people's Pull Requests are clustered apart and never mixed with Corrections.

## Considered Options

- **Widen Correction to cover Review Comments**: one term and one cluster type, but Corrections per Task would start counting review traffic that has no Task, and Pilot Verdicts would shift meaning.
- **Count every Review Comment**: simpler, but a comment the author argued down, or quietly ignored, would teach agents something nobody agreed to.
- **Ignore bot reviewers entirely**: safe, but it would lose the signal of people acting on a bot's point. Instead, bot Review Comments can strengthen a Correction Cluster but never start one, so habitlore never just copies a bot's configuration.

## Consequences

Deciding Upheld needs the thread, reactions and later code, judged by meaning during Analysis. The Repeat Rule counts Pull Requests alongside Sessions. Pull Requests are not linked to the Sessions that wrote them yet, so Evidence cannot say whether a Review Comment hit agent-written code.
