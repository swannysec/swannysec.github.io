---
published: true
title: Starting Small with Threat Intelligence - Pt. 1
layout: post
tags: [Threat_Intelligence, How_To]
---
In my last [post](https://swannysec.net/2015/11/07/talking-point-threat-intel-is-not-an-all-or-nothing-proposition.html), which appears to have been eons ago, I asserted, contrary to the popular narrative, that I believe it makes a lot of sense for small or still-maturing information security programs to build a threat intelligence capacity.  While this may not be a popular opinion, I know that smaller operations can benefit from a right-sized threat intelligence program because I'm in the process of building one currently and there have been tangible results.  I also mentioned in my last post that I would provide some details on getting started with threat intelligence.

To begin, one must understand the basics of threat intelligence.  I provided the following definition, from Gartner, in my last post:

> “Threat intelligence is evidence-based knowledge, including context, mechanisms, indicators, implications and actionable advice, about an existing or emerging menace or hazard to assets that can be used to inform decisions regarding the subject's response to that menace or hazard.”

This blog post will not attempt to teach you all the basics; instead, the focus is on how to start digesting and operationalizing intelligence.  Other sources have provided background knowledge more comprehensively; in order to bolster your understanding, I recommend the following:

| Resource | Description |
|:--------------|:-----------------|
| [The Definitive Guide to Cyber Threat Intelligence](https://cryptome.org/2015/09/cti-guide.pdf) | From iSIGHT Partners.  Nice overview, comprehensive and well formatted. |
| [Threat Intelligence: Collecting, Analysing, Evaluating](https://www.mwrinfosecurity.com/system/assets/909/original/Threat_Intelligence_Whitepaper.pdf) | From MWR InfoSecurity and CERT-UK/CPNI in the UK.  A bit more of a high-level overview, still an excellent starting point. |
| [Intelligent Intelligence: Secrets to Threat Intel Success](https://speakerdeck.com/davidjbianco/intelligent-intelligence-secrets-to-threat-intel-success) | From [David J. Bianco](https://twitter.com/DavidJBianco) at Sqrrl.  Pay particular attention to his "Pyramid of Pain" and the work/knowledge flows he outlines. |

With the barebones basics established, how tall must one be to ride?  In my estimation, you need a good head on your shoulders, a general understanding of the security space, threats, and countermeasures, and enough technical ability to understand and use the data you will be presented.  You don't need a complete infosec program or a whizbang black box racked in a datacenter somewhere.  In fact, you don't really need anything other than an internet-enabled device and your brain to begin digesting threat intelligence.  

I recommend that anyone interested in threat intel start simply by seeking out and reading published threat reports from companies such as FireEye, Palo Alto, or Symantec.  A large repository of these reports can be located on Github [here](https://github.com/kbandla/APTnotes).  In particular, check out the following as excellent examples:

| Resource | Description |
|:--------------|:-----------------|
| [Mandiant's APT1 Report](http://intelreport.mandiant.com/Mandiant_APT1_Report.pdf) | Somewhat dated, but the standard that many threat reports follow to this day. |
| [Symantec's Report on the Dyre Banking Trojan](https://www.symantec.com/content/en/us/enterprise/media/security_response/whitepapers/dyre-emerging-threat.pdf) | Top to bottom look at a family of financial malware. |
| [Palo Alto Unit 42's Recent Look at Angler's Continuing Maturation](http://researchcenter.paloaltonetworks.com/2016/01/angler-exploit-kit-continues-to-evade-detection-over-90000-websites-compromised/) | Really nice in-depth look at a specific exploit kit, showing, among other things, how bad actors utilize counter-intelligence to harden their malware and prevent blue team research. |

I also recommend that one follows the twitter feeds and blogs of people who do this kind of work for a living and share what they can with the rest of us.  Check out [Christian P.](https://twitter.com/CYINT_dude) at his [blog](http://www.cyintanalysis.com/) and [Scott Roberts](https://twitter.com/sroberts) at [his](https://sroberts.github.io).  Learn how they approach threat intel and take their lessons learned into account as you begin your journey.  Finally, check out a few of the intel sharing repositories available without expenditure.  I recommend Alienvault's [Open Threat Exchange](https://www.alienvault.com/open-threat-exchange) for the general public and CIRCL's [MISP](http://circl.lu/services/misp-malware-information-sharing-platform/) instance if your organization is eligible.  These are both excellent sources of human-readable threat intelligence data, but also offer ways to automate collection as you grow into your new threat intel capability.

The key to starting with simple human consumption of publicly available threat intelligence is that one becomes accustomed to how the data is collected, analyzed, and presented.  As you digest the information in the reports, start thinking about your own organization.  How would you identify this activity on your network?  Have you seen any evidence of this in logs?  Can you prevent this activity?  Can you put proactive alerting in place?  This is valuable as a mental exercise and can be translated to real action as your understanding and tools mature.  You might even stumble across one of these threats in your organization in real-time.  At the most basic level, even if you do nothing further, you are putting threat intelligence to good use by completing this mental exercise and better arming yourself as an analyst with things to watch for and build defenses against.

Ultimately, no matter how you consume and process threat intelligence data, the goal should always be to provide a tangible benefit to your organization by altering or augmenting decision making around both preventative and detective security measures.  Learn from the lessons others have endured and prevent your organization from being the victim of something that is already well documented and understood.

In part two, we'll take the next step by introducing tools such as Bro IDS, Splunk, and CIF, that will facilitate the automated collection and processing of some types of intelligence data.  As always, I'm eager to hear your feedback; please reach out [@swannysec](https://twitter.com/swannysec).