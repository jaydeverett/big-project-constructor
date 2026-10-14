---
name: big-project-constructor
description: Project memory for non-technical builders. Use when someone is starting a big project (a business, book, podcast, renovation, job search, app, or anything that will take weeks), wants to pick up where a previous conversation left off, keeps losing track of what was decided, asks how to stay organized across many chats, or says "wrap it up" or "end session". Sets up a project folder with a topic structure, an instruction file the assistant reads every session, a running log and a current-state summary per topic, and an end-of-session ritual that saves everything for next time. Not for one-off questions, a single coding task, or a project that fits in one conversation.
---

# Big Project Constructor

A method for running a weeks-long project with an AI assistant without losing the thread between conversations. The assistant's memory becomes a folder of plain files. Every session starts by reading them and ends by updating them.

Three parts:

- **One instruction file** at the project root (`CLAUDE.md` in Claude Code, `AGENTS.md` in Codex) that the assistant reads automatically. It says how this project works.
- **One pair of files per topic.** `Brainstorm.md` is an append-only log of every session. `Master.md` is the distilled current state, always readable on its own.
- **One ritual.** The user says "wrap it up" and the assistant updates the files, writes a session summary, and produces the prompt that starts the next session cold.

Everything the assistant needs is in this folder:

| Path | What it is |
|---|---|
| `assets/instructions-template.md` | The project instruction file, with `{{PLACEHOLDERS}}` to fill at setup. Carries the full session workflow. |
| `assets/brainstorm-skeleton.md`, `assets/master-skeleton.md` | Empty per-topic files. |
| `assets/process-meta-notes-template.md` | The workflow-observations log, with a how-to at the bottom. |
| `assets/example/` | A worked example (two sessions of a fictional podcast project). |
| `assets/hooks/wrap-reminder.sh` | An optional, inert Claude Code hook that nudges the user to wrap. |
| `references/workflow.md` | Why the ritual works, what to do when it breaks, and how to work with more capable models. |
| `references/faq.md`, `references/starter-prompts.md`, `references/optional-patterns.md` | Answers, paste-in prompts, and patterns for bigger projects. |

## First, work out which situation you are in

1. **The project is already set up.** The current folder has a `CLAUDE.md` or `AGENTS.md` that mentions Big Project Constructor and at least one numbered topic folder. Do nothing special: that file carries the whole workflow and you are already following it. If the user says "wrap it up," follow its wrap-up section.
2. **The user has a project folder but it is not set up yet.** Either they copied the template (the folder contains this very file under `skills/big-project-constructor/`) or they installed this as a plugin and opened an empty or unrelated folder. Run **Setup** below.
3. **There is no file system.** You are in ChatGPT on the web or mobile, with no folder to write into. Run **Setup** with the adjustments in **Working without a file system**.

## Setup

Walk the user through five questions, one at a time, then build the project. Rules that hold throughout:

1. **One question at a time.** Do not batch. Wait for the answer before moving on.
2. **Confirm after each answer.** Echo back what you understood in one or two sentences and let them correct you.
3. **Plain language.** Many users are non-technical. If a technical term is unavoidable, define it inline.
4. **Take a position when asked.** If the user asks "what should I pick?", recommend one thing with one sentence of reasoning.
5. **Be quick.** Five minutes, not thirty. "Good enough" moves on.

### Step 1 — Welcome

On the user's first message, whatever it says, greet them and explain what happens next:

> "I'm going to ask you five quick questions to set this up as a real project. By the end, about five minutes, you'll have a working project structure customized for you, and we can either start the first session immediately or stop and come back later. Ready?"

Wait for a yes.

### Step 2 — What is this project?

> "First question: in a few sentences, tell me what this project is. What are you working on, who is it for, and what would a good outcome look like? A rough answer is fine; we can sharpen it later."

Extract a short name (one to three words) usable as a title and a folder name, and a two-to-four-sentence description. If the answer is vague ("a podcast"), ask one follow-up: "What's the angle? What makes it specific?" Confirm: "So this is **[NAME]**: [one-sentence summary]. Sound right?"

### Step 3 — What phase?

> "Second question: what phase is this in right now? Concept (still figuring out what it is), Design (concept is clear, planning the details), Build (actively making it), Launch (getting it in front of people), Iteration (it's out and you're improving it), or Open-ended (an ongoing thing). One word is enough."

Confirm and move on.

### Step 4 — What are the major topics?

This is the most important question; it sets the folder structure.

> "Third question: what are the major topics or phases of this project? Pick four to seven. They'll become the top-level folders. They can be phases you work through in order, or independent areas that all happen in parallel. If you're not sure, I can suggest some based on what you told me."

If they want suggestions, propose four to six based on the description and phase. Phase-based naming for sequential projects (`Concept`, `Design`, `Build`, `Launch`); domain-based for parallel ones (`Strategy`, `Product`, `Operations`, `Marketing`); audience-based where that fits (`Internal`, `Customers`, `Partners`); for creative work (`Foundation`, `Production`, `Distribution`, `Audience`); for a service business (`Positioning`, `Offers`, `Marketing`, `Operations`, `Clients`); for an investigation or research project (`Sources`, `Timeline`, `Actors`, `Patterns`, `Open_Questions`). Accept the user's list unless it is obviously off (fifteen topics, or one topic that is clearly too narrow). Confirm the final list with the numbered folder names.

### Step 5 — Where do you want to start?

> "Fourth question: which topic do you want to work on first? Most projects benefit from starting at the foundational one, but you can start anywhere."

Do not renumber folders to match. Confirm.

### Step 6 — Anything else?

> "Last question: anything project-specific I should know that would shape how I help? Principles you've already decided, terminology unique to this project, people you sync with regularly, anything load-bearing. If nothing comes to mind, say 'nothing'; you can add it later."

Capture the answer for the Project-Specific Notes section. Two things worth prompting for if they do not come up: whether anything made here will go out under the user's name to other people (the instruction file treats those as the user's documents), and whether the material is sensitive (which decides whether the folder should ever leave the machine).

### Step 7 — Confirm the plan

> "Here's what I'm going to set up:
> **Project:** [Name]
> **Description:** [description]
> **Phase:** [phase]
> **Topic folders:** [list]
> **Starting with:** [topic]
> **Project-specific notes:** [notes, or 'none for now']
> Shall I create this?"

### Step 8 — Build the project

Once confirmed:

1. **Render the instruction file.** Read `assets/instructions-template.md` and substitute: `{{PROJECT_NAME}}`, `{{SETUP_DATE}}` (today, YYYY-MM-DD), `{{PROJECT_DESCRIPTION}}`, `{{PROJECT_PHASE}}`, `{{TOPIC_FOLDER_TREE}}` (one entry per folder, each with `Brainstorm.md` and `Master.md`, in tree form), and `{{PROJECT_SPECIFIC_NOTES}}` (readable prose or bullets; if "nothing", write `_None yet. Add notes here as the project evolves._`). Write the result to **`CLAUDE.md`** if you are Claude Code, or **`AGENTS.md`** if you are Codex. In Codex, also replace "Claude Code" with "Codex" and "Claude" with "Codex" in the rendered text, and skip the wrap-reminder offer in Step 9 (the hook is Claude Code-specific).
2. **Create the topic folders.** `01_Topic_Name/` style: two-digit prefix, Title_Case, underscores for spaces. In each, create `Brainstorm.md` from `assets/brainstorm-skeleton.md` and `Master.md` from `assets/master-skeleton.md`, substituting `{{TOPIC_NAME}}` (with spaces) and `{{TOPIC_DESCRIPTION}}` (a one-line description you write from the topic name).
3. **Copy the supporting files into the project.** `assets/process-meta-notes-template.md` to `Process_Meta_Notes.md` at the root. `references/` to `docs/`. `assets/example/` to `.bpc/example/` and `assets/hooks/` to `.bpc/hooks/` (a hidden folder; the instruction file points at these paths).
4. **If the user copied the template** (this file is at `skills/big-project-constructor/SKILL.md` inside their project folder), remove the template scaffolding so only their project remains: `skills/`, `plugin.json`, `.claude-plugin/`, `LICENSE`, and whichever first-run pointer you did not overwrite (`AGENTS.md` under Claude Code, `CLAUDE.md` under Codex). Replace `README.md` with two lines: the project name and the one-sentence description. If you installed as a plugin, there is nothing to remove.
5. **If git is available and the folder is not a repository,** offer to initialize one. Sensitive projects stay local or in a private repository; say so.
6. **Tell the user what exists now:**

   > "Setup complete. Here's where things are:
   > - `CLAUDE.md` (or `AGENTS.md`): the project's instruction file, read automatically every session
   > - `01_…/`, `02_…/`: your topic folders, ready for content
   > - `Process_Meta_Notes.md`: for observations about the workflow as you go
   > - `docs/`: references on the workflow itself
   > - `.bpc/example/`: a worked example you can read for reference, delete anytime
   >
   > Want to start your first session now? It would be on **[STARTING_TOPIC]**, and I'd begin by asking the first foundational question. If you'd rather come back later, paste this at the start of your next session:
   > ```
   > Start session on [STARTING_TOPIC]. Read [instruction file] and [folder]/Brainstorm.md, then ask me one question at a time to begin filling in this topic.
   > ```"

### Step 9 — Offer the wrap reminder (Claude Code only)

One yes/no offer, not a sixth question. "No" is a fine answer; do not press.

> "One optional thing. The whole workflow depends on you typing 'wrap it up' before you close a session; that's the step that saves your work, and it's the easiest one to forget. I can install a small reminder that nudges me to offer a wrap-up when a session has run long or the conversation gets full. It's a commented script at `.bpc/hooks/wrap-reminder.sh`; it only talks to me, never blocks anything, and doesn't touch the network. Want it on?"

If yes, write `.claude/settings.local.json`, merging with any existing content rather than overwriting:

```json
{
  "hooks": {
    "SessionStart": [{ "hooks": [{ "type": "command", "command": "\"$CLAUDE_PROJECT_DIR/.bpc/hooks/wrap-reminder.sh\"" }] }],
    "Stop":         [{ "hooks": [{ "type": "command", "command": "\"$CLAUDE_PROJECT_DIR/.bpc/hooks/wrap-reminder.sh\"" }] }]
  }
}
```

Then: "Done. It takes effect next session. Ask me to remove it anytime, or change the threshold with `BPC_WRAP_AFTER_TURNS` (default 25)."

Why the file is local and never committed: it is gitignored, so it stays on this machine. Hooks are shell commands that run automatically, and a template that shipped them pre-wired would execute code on everyone who copied it before they had looked at it. The script ships inert and asks first.

### Step 10 — Start the first session, if they want

Transition into the starting topic. Ask what they consider the most important foundational question for it, then follow the workflow in the instruction file you just wrote: one question at a time, flag decisions as they happen, wrap on "wrap it up."

### Failure modes

- **User wants to skip a question.** Mark it "to be filled in later" and move on.
- **Long, rambling answer.** Extract the signal, summarize, confirm, move on.
- **More than seven topics.** Suggest grouping. If they insist, accept and note that long folder lists get hard to navigate.
- **User asks about advanced patterns during setup.** Say they exist in `docs/optional-patterns.md` and can be added later. Keep setup minimal.
- **Something fails during file creation.** Say clearly what failed and what state things are in. Do not continue silently.

## Working without a file system

In ChatGPT on the web or mobile there is no folder for the assistant to write into. The method still works, with the user holding the files. Run the same five questions, then:

1. **Tell the user to create a ChatGPT Project** for this work before anything else, and to do every session inside it.
2. **Render the instruction file as text** and have the user paste it into the Project's instructions. Replace "Claude Code" with "ChatGPT" and "Claude" with "ChatGPT" in the rendered text. Delete the wrap-reminder and git steps; they do not apply.
3. **Produce `Brainstorm.md` and `Master.md` for the starting topic as downloadable files** and tell the user to add them to the Project. Other topics get theirs when work there begins.
4. **At every wrap-up, produce the updated files again as downloads** and tell the user to replace the old versions in the Project. The next-session prompt names the files to read.

Be plain with the user that this is the lighter version: the assistant cannot edit the files in place, so the user's discipline about replacing them is what keeps the memory accurate. If they later move to Claude Code or Codex, the same files drop into a folder and the full method takes over.

## The working rules, in brief

The instruction file carries these in full. They are the ones that matter most with capable models, which tend to do too much rather than too little:

- **Ground before proposing.** Read the actual work before designing on top of it.
- **One question at a time.** Factual gap-fills can be batched; judgment calls cannot.
- **Write decisions to the file the moment they are made,** not at wrap-up.
- **Flag once, then respect the decision.**
- **When corrected, concede fast, re-derive, and check what else the error touched.**
- **Prescribe, never apply, on anything that goes out under the user's name.**
- **Verify, then declare.** "I made the change" and "the change works" are different claims.
- **Nothing important stays in the chat.** Anything pasted in is written to a file verbatim first.
