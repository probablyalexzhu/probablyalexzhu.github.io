---
title: "Building the Notetaker of All Time"
tags: [projects, software engineering, fullstack, thoughts]
date: 2026-05-08
description: "A cross-device floating notes app and some technical lessons"
showDate: true
showWordCount: true
showReadingTime: true

# summary: "Hi! My name is Alex Zhu."
showSummary: true
showAuthor: true
showTableOfContents: true
showComments: true
showPagination: true
invertPagination: true
showTaxonomies: true

draft: false
---

A few months ago, I [wrote about momentum](https://probablyalex.com/blog/rolling-downhill/), finding the right hill, and rolling down it. Right around then, I started building something I'd been wanting to make for a while: **a minimalist note-taking app with realtime cross-device sync, like Raycast Floating Notes but with sync**. With sync between my Mac and my iPhone, I'd stop DM-ing myself reminders and finally have a shared "L1 cache" on hand.

I spent the next month building noat on nights and weekends after work, using project-based learning to pick up some new skills. Now that I'm back home, I can write about how it went.

![Typing on the iPhone, watching the desktop update via Supabase realtime](sync-demo.gif "Cross-device sync via Supabase Postgres Changes")

## What's noat?

In a noatshell:
- TWO connected apps: Translucent floating window on macOS (Tauri + Rust + React); native iOS/Android app on phone (Expo)
- Global shortcut (Option + /) to toggle desktop window visibility + 5 colour themes
- Local-first SQLite, so it works fully offline
- Cross-device sync in under 100ms via Supabase Postgres Changes

I felt like the existing ways people write notes to themselves had too much friction. Notion is beautiful but somewhat laggy especially on start, and it doesn't work very well offline. Apple Notes is decent, but the syncing behaviour often doesn't show what you've written on another device until you start typing something new. And the fact that we're DMing ourselves in Discord or iMessage is a sign that we need a better solution. So I sought out to make the notetaker of all time, [noat](https://github.com/probablyalexzhu/noat).

The floating window that you can open with keyboard shortcut is the lowest friction way to take notes in my opinion, like sticky notes. And on mobile, the keyboard auto-opens for you when you open the app, to reduce the clicks required to start typing.

## The Development Process

I had an empty merch notebook from work, so I started using it to plan noat. It helped to be able to quickly draft up designs, draw architectural diagrams, and focus on the big picture instead of the details. It was also enjoyable to draw on paper again!

![Sketching the UI and the implementation side-by-side](thumb.jpg "Sketching the UI vs the implementation side-by-side")

During the development of noat, I attended Claude Code's first birthday party and came back wanting to level-up my use of Claude, i.e. running agents and subagents in parallel, plus the superpowers plugin, /insights, and more. I used this project as a chance to practice and learn. Since then, I've started using [Conductor](https://www.conductor.build/) as well for my workflow, which has been a great addition!

With Claude in the loop, I picked up a lot of new languages and technologies faster:
- **Rust** on the Tauri app
- **mobile development** w/ Expo. Running noat on my actual iPhone felt sick
- **Supabase realtime** subscriptions, replica identity, etc.

Talking to friends during the development was also great fun. I got to practice my asking-customers-what-they-want muscle without leading them to answers I wanted to hear, such as what was missing from their current workflows. I heard things like Todoist is overengineered, and that others were happy with just texting themselves already! I took what I heard and filtered it down to the core essentials, wanting to keep things minimal and intuitive.

When I asked my friend Taira for her takes, she even brought noat up to an investor, who of course said that it should have AI and be built for agents! I feel like not everything has to be made for agents yet; there are personal things that humans benefit from doing themselves still.

She also suggested I apply to Compound VC's Reverie Grants, at which point I discovered they already had a company named Noat in their portfolio — a nicotine company. 🚬

## Technical Learnings

### Polling to realtime

The first version was a 500ms poll loop with a 3s push debounce before pushing local changes to the server. AI allows us to prototype quickly, so even though I knew polling was unideal, it was quick to implement and try anyways. Polling had a couple problems:
- Polling drains battery in theory
- Inbound latency was up to 3.5s total

The fix was to migrate from polling to **Supabase Realtime**, a websocket subscription that pushes row-level events as soon as the database commits them. Pull became immediate, overriding local changes (<100ms). Push kept the debounce so keystrokes still get batched into one network call vs tons as you are still typing.

![The "Remote Change Detection v1" page — polling crossed out, "Realtime Supabase! GOOD!" circled](notebook-sync.jpg "The  page where I gave up on polling")

### The delete bug

Right after migrating to realtime, deleting notes stopped syncing between devices, i.e. you would still see them on the other device. Inserts and updates worked fine, but if you deleted a note on the desktop, your phone kept showing it.

The cause: Supabase's default `REPLICA IDENTITY` for a Postgres table only includes the primary key in DELETE payloads, no `user_id`. When we were looking for updates on what notes were deleted, we were filtering by user ID as well, so that you could only delete your own notes and not other people's. But since there was no user_id in the payload, the delete wasn't being picked up.

To fix this, we stopped filtering DELETEs on user_id. Because a user only has their own notes, deleting by primary key is safe without verifying ownership anyways. 

Additionally, the client re-pulls the current state from Supabase and reconciles any local rows that no longer exist upon refocus of the app. This was necessary for syncing changes that happened offline anyways, and happened to be an extra layer of syncing that helped with this delete bug too.

### Monorepomaxxing

I started with just the mobile app, so I had to figure out how to add the desktop app and consolidate them into a monorepo. Having only one repo means one area to focus your attention, fewer PRs needed, one place to run commands, and one place for Claude to get all its context. This was a fun way to learn how to manage different dev environments all in one place.

```
noat/
  apps/
    desktop/        # Tauri (Rust + React + Vite)
    mobile/         # Expo / React Native
  packages/
    sync/           # @noat/sync — Supabase client + shared types
  package.json      # workspaces: ["apps/*", "packages/*"]
```

`@noat/sync` exports the Supabase client and shared types so both apps stay in sync (no pun intended). The actual sync *logic* stays per-platform — `expo-sqlite` is synchronous and Tauri's `plugin-sql` is asynchronous, so they can't share function signatures.

![noat on macOS](desktop-hero.png "I started using noat myself in day-to-day while I had the dev server running anyways")

## Ending on a positive noat

Once I had a working prototype of noat, the remaining work to get it into the real world for everyone else was auth, app store distribution, stamping out bugs, and other unglamorous shipping stuff. But I had already hit the learning goals I set for myself for this time, such as learning cross-platform architecture, a Tauri app with native macOS integration, and realtime syncing. Thus, I wrapped up this project to work on other things.

After noat, I started shipping [debatecomps.com](https://www.debatecomps.com/), a directory of debate tournaments and opportunities for the global debate community. It started as an idea we explored in a software engineering capstone course last year, but it was too useful to leave unfinished. My debate partner Advait and friend Acon worked to expand our data sources into Canada and India, the latter of which now drives most of our traffic. In our first month after announcing it on Facebook, we had 700+ visitors and great feedback from debaters internationally.

*Updated on July 24, 2026 for clarity and some additional thoughts*