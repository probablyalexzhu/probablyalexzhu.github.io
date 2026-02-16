---
title: "Five Learnings from My Shopify Internship"
tags: [thoughts, waterloo, co-op, work, tutorials]
date: 2025-09-12
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

I wanted to share five impactful learnings I was lucky to discover during my co-op at Shopify, one of the biggest tech companies in the world and one with a great engineering culture. Thanks to all the wonderful people I learned a ton from for making this an amazing internship!

## 1. Atomic Commits ⚛️
Each git commit one makes should represent one unit of work, making it an atomic commit.

It's a subjective question that I discussed a lot with my mentor: what exactly is an atomic commit? **My definition is: a small, complete unit of work that shouldn't break existing functionality.**

- This makes it revertible in case of needing to roll back, as well as reviewable as one complete piece of work.
- Tests for new code are usually considered to be part of the same unit of work, and thus the same PR
- Some developers value atomic commits a lot, while others care more about clear PR descriptions. It depends on the team and its workflow!

Read more about atomic commits [here](https://dev.to/samuelfaure/how-atomic-git-commits-dramatically-increased-my-productivity-and-will-increase-yours-too-4a84)

## 2. Clear PR Titles ✍️
Justin D. Harris taught me this one. A clear PR title helps when reviewing history as well as giving reviewers quick context (especially in shared repos). Follow a formula; a good one is:

**[Tag] Imperative mood description of change**

![Let me be clear](https://i.redd.it/285ffeha20191.gif "Let me be clear")

## 3. Keep Open Files When Switching Branches 🗂
On Cursor and VSCode, a common frustration is having to close/reopen tabs when switching between branches, costing time and focus. A feature to help with this recently quietly shipped, so many developers don't know about it yet. In settings, search for **scm.workingSets.enabled** and toggle this on. Now, when switching between branches, the workspace of tabs will be preserved for each branch.

I found and shared this one on the public Shopify Slack, where nearly 50 people reacted and presumably found it useful!

Find the GitHub issue for this feature [here](https://github.com/microsoft/vscode/issues/35307).

## 4. Claude Code Planning Mode 🤝
Firstly, Claude Code > Cursor, especially for non-trivial changes. It has a deeper understanding of complex codebases, better agentic debugging and investigating capacities (running commands, grep, writing test files, etc.), the terminal workflow is intuitive for devs, and it uses powerful LLM models. If you can, use Claude Code! You can use it alongside and within Cursor, but you'll find that you won't be using Cursor Chat as often anymore.

Claude Code has a useful planning mode to keep AI from going off the rails (very important to keep the human in the loop!), where it comes up with a plan first then asks for approval for write access. You can switch this mode on with shift+tab. Then, you can come up with and revise plans with Claude to increase your one-shot rate and avoid the painful work of undoing rogue AI code changes later.

Read the docs [here](https://claudelog.com/mechanics/plan-mode/).

## 5. Be Less Defensive 🪷
This is probably the most important on this list, and it's a non-technical human skill. Especially early in your career, you don't have to be defensive around your code because you're allowed to make mistakes! People give feedback and criticism to create the best product possible, not to flex on you.

Concretely, when receiving feedback, don't default to explaining your own rationale and make assumptions. Instead, **ask them to clarify the reasoning for their feedback.**

Similarly, people often have strong emotional connections to their work, which is good because it allows them to dedicate and put time and care into it! But those connections need to be severed when it is decision time and your solution may not be used, e.g. deciding what the objectively best code solution is for a team project. It can be difficult to let your work be thrown out, but the frame that "ideas don't belong to people, they exist nebulously and some people just happened to find them first" can make it easier to let go.

In the end, you want to be considered a great open-minded learner, and it's a productive mindset especially when you're surrounded by seasoned engineers who can provide highly valuable feedback.

At the same time, **remember to give positive feedback!** From my own experience, it's really nice to know what you're doing well so you can keep doing it, be more confident in owning code and grabbing new tickets, and it makes it easier to accept future critique. People really remember when you give them based compliments! Remember also to provide critique and not criticism; focus on promoting understanding and improvement, rather than conveying disapproval and focusing on faults.

![Working in the Toronto office, listening to Larry June](IMG_0324.JPG "Working in the Toronto office, listening to Larry June")