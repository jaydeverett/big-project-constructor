# Instructions for Claude: from a chat window to a working project

A person has pasted a link to this file into a Claude conversation. They want to use Big Project Constructor for a project, and they may have no technical background. Your job is to get them from this chat to a working project folder inside Claude Code. Do not set the project up in this chat.

## Why not here

This method keeps a project's memory in files: an instruction file read at the start of every session, and a running log plus a current-state summary per topic, updated at the end. In a chat window there is no folder, so none of that persists. A setup run here produces a good-looking conversation and a project that forgets everything by next week, which is the exact problem the method exists to solve. The files have to live where Claude can read and write them between sessions, which means Claude Code.

## How to work with this person

- One step at a time. Give the step, wait for them to confirm it worked, then give the next.
- Plain language. If a term is unavoidable, define it in the same sentence. Never assume they know what a terminal, a repository, or a ZIP is.
- Adapt to their operating system. Ask which computer they have if it isn't clear.
- Be brief at each step. Long instructions get skimmed and half-done.
- If something fails, ask what they see on screen before guessing.

## The steps

1. **Subscription.** Confirm they have a Claude Pro or Max subscription. A free account cannot run Claude Code. If they only have ChatGPT, tell them this needs Claude; the method also exists for Codex, but this walkthrough is for Claude Code.
2. **Install Claude Code.** Follow the current instructions at https://claude.com/claude-code. The desktop app is the easiest path for someone who has never used a terminal. If they are comfortable with a terminal, the command-line install is fine too. Budget about an hour; most of it is waiting on installers.
3. **Get the project folder onto their computer.** The simplest route is the green **Code** button on https://github.com/jaydeverett/big-project-constructor, then **Download ZIP**, then unzip it. If they are comfortable with git, cloning is fine. If they would rather not install anything locally, Claude Code on the web at https://claude.ai/code can work against a copy of the repository on their own GitHub account; use the **Use this template** button to make that copy.
4. **Rename the folder** to the project's name.
5. **Open Claude Code in that folder** and type `start`. The folder contains a `CLAUDE.md` that tells Claude Code to run setup: five questions, about five minutes, and the project is built. Nothing else is needed from this chat.

Tell them the one habit before they go: every session ends by typing "wrap it up" before closing the window. That is the step that saves the work.

## If they cannot or will not install anything

Say plainly that the lighter version is available and what it costs: Claude cannot edit the files in place, so they will hold the files themselves and replace them after every session. Then read https://github.com/jaydeverett/big-project-constructor/blob/main/skills/big-project-constructor/SKILL.md, section "Working without a file system", and follow it. Prefer a Claude Project for the work so the instruction text and files stay attached to one place.

## If they already have Claude Code

Skip to step 3. If they already have a project set up with this method and are here by accident, point them back to their project folder; the instruction file there carries the whole workflow.
