# A Team Library is a private git repository, not a server

A Team's Shared Suggestions live in its Team Library: one private GitHub repository per Team, with one readable Markdown file per Shared Suggestion (frontmatter for kind, sharer, state, Evidence summary and Measuring; the format-neutral body below). Each person's habitlore reads it on every run and writes one confirmed share at a time with that person's own GitHub access, pushing to the default branch, or opening a Pull Request when the branch is protected. habitlore runs no server and has no account of its own, so local-first holds: the only thing that leaves a machine is a Shared Suggestion its person confirmed. habitlore refuses a public repository, because that would turn sharing with a Team into publishing.

## Considered Options

- **Commit into the code repository** (`.claude/skills`, `CLAUDE.md`): nothing new to set up, but teammates install it on their next pull, skipping the Pending review, and it drops the Evidence summary and Measuring and ties a Team to one Project.
- **A Claude Code plugin marketplace repository**: familiar, but Claude-only, and it also installs without Pending.
- **A self-hosted habitlore server or a habitlore-run cloud**: real accounts and live Measuring across a Team, but servers before value is proven, and the cloud takes data out of the person's hands.

## Consequences

Withdrawal marks a file Withdrawn and does not delete it; git history keeps everything ever shared, and the share preview says so. A new version replaces the same file and reaches teammates who Accepted it as a Pending update to their copy. Reading repository access is the first sign of Team membership. A hosted backing behind the same Team Library stays possible later, for example for live Measuring across a Team; whether it is paid is the open-core boundary's call.
