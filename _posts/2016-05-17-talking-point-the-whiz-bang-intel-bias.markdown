---
published: false
title: Talking Point - The Whiz-Bang Intel Bias
layout: post
tags: [Talking_Point, Threat_Intelligence]
---
I recently had an interesting conversation with a couple of people from the threat intelligence community around the idea of adversary innovation.  Essentially, someone linked to a twitter blurb from a recent convention or trade show where the speaker mentioned that we, as defenders, need to innovate faster because our adversaries are doing it every day.

The immediate reaction, from a couple of very smart people who I consider to be mentors, as well as my own reaction, was that the idea was hogwash; attackers are lazy like the rest of us and only innovate when forced to do so.  This makes sense, right?  Humans, as a species are inherently lazy, and I know for a fact that most of those involved in technical fields loathe extraneous effort.  So, this idea that attacker methods are constantly evolving and we must rise to meet that challenge is surely patently false, correct?

Upon further reflection, I decided that our initial instinct was in actuality incorrect, and may, in fact, indicate a bias on our part.  While there are certainly those attackers out there who will innovate only when absolutely forced to do so, and many who never do at all, I think these may represent a smaller sample of the total population than we realize.  Those working in or otherwise involved in the serious study of threat intelligence tend to dwell in the land of the APT.  We eat, sleep, and breathe cyber-espionage, state-sponsored actors, and super-sophisticated financial crime syndicates.  We do this because it's our job, because it's what keeps the lights on, because it's fascinating, or maybe just because we all secretly imagine ourselves to be Jack Ryan.

[JackRyan](https://swannysec.net/public/jackryan1.jpg)

The reality, however, is that these kinds of threats probably represent a fraction of what the majority of the world contends with every day.  In fact, for most, the biggest threat comes from financially-motivated commodity malware.  The ransomware industry (and it certainly qualifies as an industry at this point) and banking trojans are likely responsible for far more damage to the worldwide economy than APTs and other sophisticated attacks will ever be.  This year's Verizon DBIR supports this conclusion, as summarized perfectly by [Rick Holland]() below:

[RickDBIR](https://swannysec.net/public/rickdbir1.jpg)

The shocking part of this realization, for me, came when I reflected on just how much innovation actually occurs in the malware industry.  Take a look at any of the major ransomware or exploit kit campaigns over the last six months.  The rate of change is astounding!  I probably read two or three reports every week about how the actors behind Angler EK, Locky, TeslaCrypt, or CryptXXX have changed something in their delivery method, in their infrastructure, or their anti-detection measures.  Here are a few examples:

| Link          | Description   |
| ------------- |:-------------:|
| [How the EITest Campaign's Path to ANGLER EK Evolved Over Time](http://researchcenter.paloaltonetworks.com/2016/03/unit42-how-the-eltest-campaigns-path-to-angler-ek-evolved-over-time/)    | Excellent overview of EITest and the payload and URL scheme changes it has seen since 2014.  |
| [Your Package Has Been Successfully Encrypted](https://www.endgame.com/blog/your-package-has-been-successfully-encrypted-teslacrypt-41a-and-malware-attack-chain)      | In-depth examination of a relatively new variant of the oft-iterated TeslaCrypt ransomware.  Includes a great graphic that shows the rapid fragmentation of the ransomware industry.      |
| [Angler EK from 82.146.46[.]242 – New URI Pattern](http://www.broadanalysis.com/2016/03/08/angler-ek-from-82-146-46-242-new-uri-pattern/) | Analysis of Angler EK traffic from a particular host, showing a brand new URI pattern.      |

It makes sense that commodity malware has to innovate more often.  Their methods are simpler, more visible, and ultimately easier for defenders and their technology to defeat.  If they fail to innovate, they stop making money as signatures and patching invalidate their methods.  APT groups or those engaging in cyber-espionage?  Their methods are more complex and sophisticated, in addition to the added burden of attempting to maintain their persistence inside an organization without being detected.

[Pyramid](https://swannysec.net/public/pyramid1.png)

At the end of the day, this is a problem most simply demonstrated by David Bianco's [Pyramid of Pain](http://detect-respond.blogspot.com/2013/03/the-pyramid-of-pain.html).  In essence, the Pyramid of Pain illustrates the concept that the majority of indicators (IPs, hashes, domains) are simple and low cost/effort to either defend against or replace as an attacker while the more challenging, complex indicators like tools and TTPs are both hard to effectively defend against and costly for an adversary to replace.  Commodity malware authors and distributors simply need to change their executable or packaging or their URL-redirect/gate scheme and push the change out across their delivery network, without regard for the noise they make while doing so.  These changes live primarily at the bottom of the pyramid; they're not terribly costly for the adversary.  In the case of APTs and other sophisticated intrusions, however, most of their methods exist higher up the pyramid.  Accordingly, the cost of changing those methods, particularly while avoiding detection, is quite high.  No wonder more sophisticated adversaries innovate only when they absolutely must.

Now, armed with an understanding that the speaker we criticized initially was probably more correct than we gave him credit for, where does the bias lie and how can we combat it?  Personally, I have to remember to pinch myself now and then and be mindful of the fact that the world really isn't as full of Lotus Blossoms, PLATINUMs, and APT6s as it seems.  While those types of things are amazing brain fodder for me, my own day-to-day job is a prime example of the broader reality, which is far less exciting.

[Wizard](https://swannysec.net/public/wizard1.jpg)

That reality is that commodity malware is my organization's single largest threat (which can be just as damaging, if not more so than some APTs).  Further, the unfortunate truth is that those threats do iterate quickly.  So, sometimes, it's important to take off my whiz-bang intel wizard hat and look up from the ground; the perspective it brings is critical.  I suggest we all take that step back and try to take in a little perspective now and then.  

As always, I'd love your feedback; please reach out [@swannysec](https://twitter.com/swannysec).