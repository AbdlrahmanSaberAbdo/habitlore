# Teams share Accepted Suggestions, never what they came from

A person shares only Accepted Skills and Rules with a Team, one at a time, through a preview of the exact payload that they can edit. The payload is the title, trigger and body, an Evidence summary of counts, and optionally its Measuring result. Pending Suggestions, Workflows, Correction Clusters, Evidence links and User Message text never leave the machine, because they are built from raw Sessions and no automatic scrubber reliably strips them. The same payload is what a public marketplace would publish later, so sharing with a Team never leaks more than publishing would.

## Considered Options

- **Share Workflows or Correction Clusters**: richer for teammates, but they are made of Tasks and User Messages.
- **Consent per Project or globally**: how other tools do it (per org), but it would share a Rule drawn from a frustrated Correction without the person choosing it.
- **Recall instead of withdrawal**: would mean deleting files on a teammate's machine, which they own.

## Consequences

Sharing can be withdrawn but not recalled: a teammate who Accepted a Shared Suggestion keeps their copy, and habitlore says so when the person shares. A new version is a new explicit share, never automatic. Teammates cannot pass someone else's Shared Suggestion on to another Team.
