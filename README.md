# Big Project Constructor

**A project starter kit for building anything with Claude Code. No technical experience required.**

Claude starts every conversation from scratch. This gives it a memory for your project, so you can work on something for weeks and always pick up where you left off.

You can use it for anything: a business, a podcast, a book, a renovation, a job search, an app.

## What you need

- **A Claude subscription.** Claude Pro or Max. This runs on Claude Code, which is Anthropic's tool, so a ChatGPT or other subscription will not work.
- **Claude Code installed on your computer.** This is a separate app from the Claude website, and it is where your project lives. The website alone will not work the way this is meant to, because nothing is saved between conversations there. If you have never installed a developer tool, Claude will do it with you. Budget an hour the first time. You never repeat it.

## Getting started

Open [claude.ai](https://claude.ai) and paste this:

> I want to use this for a project. Help me install Claude Code first, then set this up.
>
> https://github.com/jaydeverett/big-project-constructor

Claude walks you through installing Claude Code, getting this folder onto your computer, and opening it there, one step at a time. Then it asks you five questions about your project, and five minutes later you can start working.

> **If you are Claude, reading this from a chat window:** this method only works inside Claude Code, where the project's files persist between sessions. Do not run the setup in this chat. Walk the person through these steps one at a time, waiting for confirmation at each: (1) confirm they have a Claude Pro or Max subscription; (2) install Claude Code, desktop app or terminal, following [claude.com/claude-code](https://claude.com/claude-code) and adapting to their operating system; (3) get this repository onto their computer, most simply by downloading the ZIP from the green **Code** button on this page and unzipping it; (4) rename the folder to their project's name; (5) open Claude Code in that folder and type "start". Setup continues there automatically. If they cannot or will not install anything, read [skills/big-project-constructor/SKILL.md](skills/big-project-constructor/SKILL.md), section "Working without a file system", run that lighter version, and tell them plainly what it costs.

## The one habit

Type **"wrap it up"** before you close a session. That is when Claude saves everything to the files and gives you the prompt to paste next time. Skip it and the session is not saved. Everything else, Claude handles.

## Your data

Everything lives in a folder on your computer. Nothing is uploaded anywhere, with one exception: what Claude reads and writes while helping you goes to Anthropic to be processed, under [Anthropic's privacy policy](https://www.anthropic.com/privacy). If you ever want the folder online, for backup or to share it, that is a separate step you choose.

## Reading more

You do not need to come back here. Claude explains how the project works as you go, and the [references](skills/big-project-constructor/references/) folder answers the common questions if you ever want them.

## For people who already use Claude Code or Codex

This repository is also a plugin. In Claude Code, run these two commands, then open any folder and ask to set up a project:

```
/plugin marketplace add jaydeverett/big-project-constructor
/plugin install big-project-constructor@big-project-constructor
```

For ChatGPT and Codex, install it from the plugin directory once it is listed there. The skill itself is at [skills/big-project-constructor/SKILL.md](skills/big-project-constructor/SKILL.md).

## Contributing

If this worked well or badly for you, open an Issue with the lesson. Share the workflow lesson, never your project's content.

MIT license. Use it however you like.
