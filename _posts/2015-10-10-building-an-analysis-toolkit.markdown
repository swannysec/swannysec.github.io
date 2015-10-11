---
published: false
title: Building an Analysis Toolkit Pt. 1
layout: post
tags: [Tools, Analysis]
---
**"A wise man without a book is like a workman with no tools." - Supposed Moroccan Proverb**

Where we're going, both knowledge (books), and analytical aids (tools) will be required.  Anyone working in security can attest to the fact that there's simply too much going on at any given time to process and store solely in one's own mind.  This is particularly true when investigating something that may lead to hundreds, if not thousands of related domains, IP addresses, e-mails, or file hashes.

Fortunately, the days of simple notepads are long behind us.  And while I still use both paper notepads and Microsoft OneNote for spur of the moment scribbling and free-form thought storage, there are now a whole host of analytical aids that serve not only to store investigative material, but to enrich that data via lookups and API integrations of varying sorts.  Such tools vary in focus, platform, cost, and complexity, so just about anyone should be able to find tools that are a good fit for their purpose, budget, and personal workflow.  

In part two of this post, I'll be covering my own personal choices for investigative tools and sharing how I set them up.  The remainder of this post, however, contains the goods: a curated list of investigative and analytical tools that I've collected over time.  Some of these are things I use daily and some are simply things on my to-do list to check out, but I think all of these have merit and are worthy of your time and attention to explore.  

The list leans toward the free/cheap side of things so there won't be a slew of enterprise-grade products contained therein.  It should also be noted that some of the tools listed likely fall into more than one category depending on the breadth of their feature sets; therefore, I have tried to give them the most logical home according to my own twisted mind.  Finally, individual threat feeds, honeypots, and tools with more specific technical purposes such as deobfuscation or reversing are largely beyond the scope of this list.  Enjoy.

## Swanny's Big List of Security Analysis Tools

**Journaling/Incident Tracking/Note-taking**

| Name | Description |
|:--------------:|:-----------------:|
| [FIR](https://github.com/certsocietegenerale/FIR) | Fast Incident Response.  Lightweight IR management platform.  Will track and correlate manually entered IOCs. |
| [SCOT](https://github.com/sandialabs/scot) | Sandia Cyber Omni Tracker.  IR management platform with robust IOC tracking/correlation and plugins for integration with other tools. |
| [RTIR](https://github.com/bestpractical/rtir) | Request Tracker for Incident Response.  Just what it sounds like.  RT with built in workflows for IR. |
| [threat_note](https://github.com/defpoint/threat_note) | Lightweight IoC tracking and enrichment, designed as a research tool. |
| [Microsoft OneNote](https://www.onenote.com/) | Great notetaking app.  Store notebooks locally, or on cloud storage. |
| [Evernote](https://evernote.com/) | Robust cloud based notetaking app with great tagging system.  Take note: No client-side encryption. |
| [Cherrytree](http://www.giuspen.com/cherrytree/) | Simple local note-taking app with an organizational system similar to Evernote. |


**Threat Intelligence/IoC Aggregation and Processing**


|:--------------:|:-----------------:|
| [I'm an inline-style link](https://www.google.com) | centered |
| [I'm an inline-style link](https://www.google.com) | are neat |
| [I'm an inline-style link](https://www.google.com) | right-aligned |
| [I'm an inline-style link](https://www.google.com) | centered |
| [I'm an inline-style link](https://www.google.com) | are neat |
| [I'm an inline-style link](https://www.google.com) | right-aligned |
| [I'm an inline-style link](https://www.google.com) | centered |
| [I'm an inline-style link](https://www.google.com) | are neat |
| [I'm an inline-style link](https://www.google.com) | right-aligned |
| [I'm an inline-style link](https://www.google.com) | centered |
| [I'm an inline-style link](https://www.google.com) | are neat |
| [I'm an inline-style link](https://www.google.com) | right-aligned |
| [I'm an inline-style link](https://www.google.com) | centered |
| [I'm an inline-style link](https://www.google.com) | are neat |
| [I'm an inline-style link](https://www.google.com) | right-aligned |
| [I'm an inline-style link](https://www.google.com) | centered |
| [I'm an inline-style link](https://www.google.com) | are neat |
| [I'm an inline-style link](https://www.google.com) | right-aligned |
| [I'm an inline-style link](https://www.google.com) | centered |
| [I'm an inline-style link](https://www.google.com) | are neat |
| [I'm an inline-style link](https://www.google.com) | right-aligned |
| [I'm an inline-style link](https://www.google.com) | centered |
| [I'm an inline-style link](https://www.google.com) | are neat |
| [I'm an inline-style link](https://www.google.com) | right-aligned |
| [I'm an inline-style link](https://www.google.com) | centered |
| [I'm an inline-style link](https://www.google.com) | are neat |
| [I'm an inline-style link](https://www.google.com) | right-aligned |
| [I'm an inline-style link](https://www.google.com) | centered |
| [I'm an inline-style link](https://www.google.com) | are neat |
| [I'm an inline-style link](https://www.google.com) | right-aligned |
| [I'm an inline-style link](https://www.google.com) | centered |
| [I'm an inline-style link](https://www.google.com) | are neat |