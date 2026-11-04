# habitlore

habitlore reads past AI coding sessions, finds the work a person keeps repeating, and turns it into Suggestions that teach their agents.

## Sources

**Harness**:
A coding tool whose sessions habitlore reads, such as Claude Code or Cursor.
_Avoid_: Provider, source, tool, agent

**Code Host**:
A service holding the person's Pull Requests and their review, such as GitHub. Not a Harness: no agent works in it.
_Avoid_: Source, forge, platform

**Pull Request**:
A proposed change on a Code Host, reviewed before it merges. Neither a Session nor a Task: it may come from one Session, several, or none.
_Avoid_: PR, merge request, change

**Review Comment**:
A reviewer's opening comment on lines of a Pull Request's diff. Replies in its thread are its context, not further Review Comments. It is not a Correction, because it is not addressed to an agent.
_Avoid_: Review, feedback, note

**Model Provider**:
The LLM service habitlore itself calls during Analysis, chosen by the user.
_Avoid_: Provider (alone), LLM, backend

**Session**:
One conversation in a Harness, from its first message to its last. Subagent runs started inside it belong to it.
_Avoid_: Conversation, chat, composer, thread, transcript

**User Message**:
A message the person typed in a Session. Text written by the agent, subagents or the Harness never counts.
_Avoid_: Prompt, turn

**Adapter**:
The part that reads one Harness's storage, or one Code Host, during a Scan.
_Avoid_: Parser, importer, connector

**Project**:
The git repository a Session worked in, including all its worktrees and subfolders. A folder outside git is its own Project.
_Avoid_: Workspace, repo, directory, cwd

## Analysis

**Scan**:
Reading Harness storage and Code Hosts into habitlore's local store. Uses no Model Provider.
_Avoid_: Import, sync, ingest

**Analysis**:
The steps that use the Model Provider: splitting Sessions into Tasks, labelling Intents, naming Clusters and writing Suggestions.
_Avoid_: Processing, mining

**Task**:
One goal the person pursued inside a single Session. A goal continued in another Session is a separate Task.
_Avoid_: Job, request, issue

**Intent**:
The purpose of a User Message: New Task, Correction, Clarification, Approval or Follow-up.
_Avoid_: Label, category, type

**Correction**:
A User Message that rejects or fixes something the agent did. Asking for more, or changing one's own mind, is a Follow-up instead.
_Avoid_: Fix, redirect, pushback

**Upheld**:
A Review Comment the Pull Request's author took: the commented code changed afterwards, or the author agreed. Pushback the reviewer accepted, or a thread closed with the code unchanged, is not Upheld. Only Upheld Review Comments become Evidence.
_Avoid_: Accepted, applied, valid

**Cluster**:
A group of similar Tasks.
_Avoid_: Pattern, group, habit

**Correction Cluster**:
A group of similar Corrections and Upheld Review Comments on the person's own Pull Requests, gathered regardless of Workflow. Review Comments from bots can join one but never start one.
_Avoid_: Repeated feedback, pet peeve

**Repeat Rule**:
The threshold a Cluster or Correction Cluster must pass before it earns a Suggestion: by default at least 3 members across at least 2 Sessions or Pull Requests within 60 days.
_Avoid_: Threshold, minimum

**Workflow**:
A Cluster that passes the Repeat Rule. A Workflow lasts across Analyses: new Tasks join it, and it is only reshaped when the person explicitly asks for a full re-cluster.
_Avoid_: Pattern, routine, habit

**Near-Workflow**:
A Cluster that does not pass the Repeat Rule yet but is big enough to show. It earns no Suggestion until it becomes a Workflow.
_Avoid_: Candidate, almost-Workflow, emerging pattern

## Suggestions

**Suggestion**:
A proposed change to how the person's agents behave, derived from a Workflow, a Correction Cluster, or a teammate's Shared Suggestion.
_Avoid_: Draft, recommendation, proposal

**Skill**:
The kind of Suggestion that is a reusable procedure an agent can follow. Skills come from Workflows.
_Avoid_: Playbook, recipe

**Rule**:
The kind of Suggestion that is a one-line standing instruction. Rules come from Correction Clusters.
_Avoid_: Guideline, preference, convention

**Evidence**:
The Tasks, Corrections or Upheld Review Comments a Suggestion was derived from, each linked to its Session or Pull Request. A Suggestion received from a Shared Suggestion has only its Evidence summary.
_Avoid_: Sources, references, citations

**Target**:
The existing Skill or Rule a Suggestion updates. Only files the person owns can be a Target; skills that come from plugins never are. A Suggestion without a Target creates something new.
_Avoid_: Base, original, parent

**Pending**, **Accepted**, **Rejected**:
The states of a Suggestion. Accepting installs it, or applies it to its Target; a Rejected Suggestion is remembered so it is not proposed again.
_Avoid_: Installed, approved, dismissed

**Scope**:
Where an Accepted Suggestion is installed: Project scope (one Project) or User scope (all of the person's work).
_Avoid_: Location, level, target

**Renderer**:
The part that turns a Suggestion into one Harness's file format.
_Avoid_: Exporter, formatter, generator

## Measuring

**Corrections per Task**:
The number of Corrections in a Task, averaged over a Workflow. The main sign that agents are improving.
_Avoid_: Error rate, friction

**Before window**, **After window**:
Two equal-length periods either side of the moment a Suggestion was Accepted.
_Avoid_: Baseline period

**Control**:
The person's Workflows and Correction Clusters that have no Accepted Suggestion, measured over the same Before and After windows, so changes that touch everything (a new model, say) are not credited to a Suggestion.
_Avoid_: Baseline, comparison group

**Verdict**:
Whether one Accepted Suggestion helped: Helped, Didn't help, or Not enough data.
_Avoid_: Result, score, outcome

**Pilot**:
The time-boxed proof that habitlore helps: the author and three colleagues, each measured for six weeks after their first Accepted Suggestion.
_Avoid_: Trial, beta, study

## Teams

**Team**:
A group of people who choose to share derived knowledge with each other.
_Avoid_: Organisation, workspace, company, org

**Shared Suggestion**:
An Accepted Skill or Rule a person chose to share with a Team, in the reviewed form that left their machine. It names the person who shared it, and it reaches teammates as a Pending Suggestion. Withdrawing it stops it being offered; copies teammates already Accepted stay theirs.
_Avoid_: Package, export, share, contribution

**Evidence summary**:
The counts that stand in for Evidence in a Shared Suggestion: how many Tasks and Sessions, over which dates, in which Harness. It never names a Task, Session, Project or User Message.
_Avoid_: Anonymized Evidence, stats

**Team Library**:
The one place a Team's Shared Suggestions live, which every member's habitlore reads. At first it is a private GitHub repository, holding one readable file per Shared Suggestion. A Team has exactly one Team Library.
_Avoid_: Hub, store, registry, repo

**Withdrawn**:
The state of a Shared Suggestion its sharer stopped offering. It stays in the Team Library's history; teammates are no longer offered it, and copies they already Accepted stay theirs.
_Avoid_: Deleted, recalled, revoked
