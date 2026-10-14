# Starter Prompts

Concrete prompts you can paste at the start of a Claude Code session. Adapt the bracketed parts to your project.

## The first session of a brand-new project

```
This is the first session for [project name]. I just finished setup. Let's begin work on [starting topic — the one you picked during setup]. Read CLAUDE.md and [starting topic folder]/Brainstorm.md, then ask me the first foundational question one at a time. I'll signal when we're done with "wrap it up."
```

(If you said yes to "start the first session now" during setup, Claude already moved into this mode — you don't need to paste this prompt for the very first session.)

## Resuming after the first session (no resume point saved)

```
Continuing work on [project name]. Read the Brainstorm and Master files in [folder name], then ask me one question at a time to keep working through this topic. Pick up from the most recent session in the Brainstorm.
```

## Resuming with a resume point

```
[Topic from the previous resume point]. Read the resume point at the bottom of [folder]/Brainstorm.md and the current [folder]/Master.md, then continue from where the resume point says to continue.
```

(In practice you usually paste the exact resume-point paragraph that Claude wrote at the end of the last session. The above is the fallback when you don't have one.)

## Starting work in a new topic folder

```
Time to start working on [topic name, e.g., "production setup"]. We've been working in [previous folder] — read its Master.md so you have the context, then read [new folder]/Brainstorm.md (currently empty) and start asking me one question at a time to fill in this topic. The first question should be about the most foundational thing we need to decide for this topic.
```

## Reviewing a topic without doing new work

```
Reading-only session. Read [folder]/Brainstorm.md and [folder]/Master.md. Then give me an executive-summary review: what's been decided, what's still open, what looks like it might be stale, and what you'd suggest tackling next. No writing to files — I want to think before deciding.
```

## Asking Claude to identify gaps

```
Read CLAUDE.md and the Master.md files in every numbered folder. Identify gaps: topics that have decisions but missing rationale, open questions that have gone stale, decisions in one folder that contradict decisions in another, topics that look like they should exist but don't. Don't fix anything — just produce the list. We'll work through it together one at a time after.
```

## A session that's running long

```
We've been at this a while. Time-check: how much more do you think we can productively cover before quality drops? If you think we should wrap up soon, say so and propose a stopping point.
```

(This is for Claude Code specifically — context window pressure is a real thing on long sessions. Claude is usually better at noticing this than you are.)

## Wrapping a session

```
Wrap it up.
```

That's all you need. Claude will produce the full set of deliverables from the workflow.

## Wrapping a session early because context is tight

```
We've covered more than I expected — let's wrap up now even though there's more we could do. Produce the standard deliverables, and in the next-session prompt, make sure to note what we didn't get to so I can resume cleanly.
```

## After a wrap, before closing the conversation

Save the **next session prompt** Claude produced. Options:

- Copy it into a notes file
- Paste it as a comment at the very bottom of the relevant `Brainstorm.md`
- Email it to yourself
- Anything else that means you'll find it next time

The next-session prompt is the highest-leverage artifact Big Project Constructor produces. Losing it costs you the next session's clean start.
