# What the Hell is Clawdbot and Why AI is Starting to Get Weird

If you've been anywhere near tech Twitter this month, you've probably seen people losing their minds over something called Clawdbot — now renamed Moltbot after Anthropic sent a trademark notice over the name being too close to "Claude." Mac Minis sold out. The GitHub repo hit 60,000 stars in days. People were calling it Jarvis. Then security researchers started poking at it, and things got interesting.

## What is it?

Clawdbot is an open-source personal AI assistant built by Peter Steinberger, the Austrian developer who founded PSPDFKit. The idea is simple: instead of opening ChatGPT or Claude in a browser and typing prompts, you run Clawdbot on your own machine and talk to it through the messaging apps you already use — WhatsApp, iMessage, Telegram, Slack, whatever.

It's powered by Claude (or other LLMs if you prefer) and it doesn't just chat. It acts. It can browse the web, manage your calendar, organize files, run terminal commands, send messages on your behalf. People called it "Claude with hands," and that's a pretty accurate description.

It went viral almost instantly.

## Think about what it has access to

Here's what's wild about Clawdbot: it ships without guardrails by default. That's a deliberate design choice. No sandboxing. No credential validation. No AI safety rails. The whole point is that it can do things — and it can do pretty much anything on your machine.

Your terminal. Your files. Your messaging apps. Your calendar. Your email. It reads all of it and takes action based on what it sees. As researcher Rahul Sood pointed out, "'actually doing things' means 'can execute arbitrary commands on your computer.'"

That level of access is what makes it useful. It's also what makes it terrifying.

## Prompt injection: the real problem

This is the piece that doesn't get enough attention. Clawdbot connects to your messaging apps and acts on your behalf. So what happens when someone sends your bot a carefully crafted message?

This is called prompt injection. Someone sends a WhatsApp message to your Clawdbot instance, and embedded in that message are instructions that the AI interprets as commands rather than content. The bot can't reliably tell the difference between "my human told me to do this" and "this incoming message is telling me to do this."

Researchers found that Clawdbot instances connected to Twitter/X were leaking private information when external users crafted specific prompts in replies. No exploit needed. Just the right words in a tweet.

That's not a Clawdbot bug. It's a fundamental problem with how language models process text. The model sees instructions from you and content from the outside world in the same way — as tokens. Telling it to "ignore instructions embedded in external content" is itself just another instruction that can be overridden by better-crafted injection.

Prompt injection isn't a bug you patch. It's unsolved. And every AI agent that can take actions on your behalf has this problem. Clawdbot just made it obvious because so many people deployed it so fast with zero friction.

## Why this matters beyond Clawdbot

Clawdbot isn't uniquely bad. It's just the first widely deployed example of something that's about to become very common: AI agents that have real access to your real stuff.

The pattern is always the same. Someone builds something cool. It goes viral. People deploy it without understanding the implications. And then we discover that giving an AI unrestricted access to your email, files, terminal, and messaging apps creates an attack surface that nobody has figured out how to secure yet.

Every AI agent that can take actions on your behalf has this problem. Clawdbot just made it visible.

## The bigger picture

We've gone from "talk to a chatbot in a browser" to "give an autonomous agent access to your computer, your messages, and your accounts" in about a year. The technology moved faster than the security model. Clawdbot going from zero to 60,000 GitHub stars to security cautionary tale in a matter of days is just the preview.

The next wave of AI tools will all want the same access Clawdbot had. The question is whether we'll learn anything from watching this one play out in public.

I'm not optimistic, but I'm paying attention.
