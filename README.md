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
> https://github.com/jaydeverett/big-project-constructor/blob/main/START.md

Claude walks you through installing Claude Code, getting this folder onto your computer, and opening it there, one step at a time. Then it asks you five questions about your project, and five minutes later you can start working.

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

## For Claude, not for you

_This section is addressed to Claude, for when someone pastes a link to this page into a chat. You can skip it._

If you are reading this from a chat window, the person wants a project set up with this method. Do not set it up here: the method keeps the project's memory in files, and a chat has nowhere to keep them. Read [START.md](START.md) and follow it. It walks the person through installing Claude Code and opening this folder there, one step at a time, where setup runs on its own.

## Contributing

If this worked well or badly for you, open an Issue with the lesson. Share the workflow lesson, never your project's content.

MIT license. Use it however you like.
