---
published: false
title: Talking Point: Threat Intel is Not an All or Nothing Proposition
layout: post
tags: [Talking_Point, Threat_Intelligence]
---
This week, I read a lot on twitter and elsewhere regarding threat intelligence and its place in an organization.  A ton of very smart people have strong opinions on this matter, and those opinions cover a wide spectrum, but one trend I’m noticing is that many believe threat intel has no place in an information security program that isn’t fully mature.  Many, including many vendors selling platforms or feeds, seem to think the only way to implement threat intel is to drop a fully operational intel capability into a complete, mature information security organization.  Many are saying that “we” as an industry need to temper our expectations on threat intel and only apply it when we’re in a position to dedicate 100% effort and resources to it.

As my grandfather would say, “we is a horse turd.”  In other words, I don’t subscribe to that way of thinking, and I’m not interested in being part of that “royal” we.  I believe threat intelligence has a place in most organizations and can provide value to smaller, less mature information security programs.

Let’s begin with a definition of threat intelligence, provided by [Gartner]( https://www.gartner.com/doc/2487216/definition-threat-intelligence) in this particular case:

> “Threat intelligence is evidence-based knowledge, including context, mechanisms, indicators, implications and actionable advice, about an existing or emerging menace or hazard to assets that can be used to inform decisions regarding the subject's response to that menace or hazard.”

There are a couple of key things to note about the definition above (which I should note is a pretty good one).  First, intelligence is comprised of a number of different types of information to include context, indicators, mechanisms, and actionable advice.  Second, note carefully the actionable part and that the remainder of the definition states that the intelligence derived can be used to inform how the subject responds to threats.

Given this information, I was taken aback to discover a tweet from an employee of one of the leading threat intelligence providers stating that considering scraping indicators from a public threat report to be good threat intelligence was "doing it wrong."  I challenge this assertion.  Working for a small organization (one security professional), I may not be able to make strategic adjustments to better align my whole organization to defend against the actor or his more complex TTPs; what I can do, however, is put those indicators to use immediately to better inform my operations.  If those indicators have matches in my environment, be they traffic logs, file hashes, or e-mails, you can bet I'm going to initiate an investigation or formal incident response.  Going back to the definition, did I not use derived intelligence to inform how I responded to a threat?  Would I have ID'ed the activity without those indicators?  Sounds like textbook threat intelligence to me!

Don't believe me?  Take it from some people who live and breathe threat intelligence, [Dmitri Alperovitch](https://twitter.com/dmitricyber) and Adam Meyers, Co-Founder and VP Intelligence respectively, at Crowdstrike.  In an excellent podcast from Down the Security Rabbit Hole, they state unequivocally that organizations can start small with "finished intelligence" that's actionable by feeding it to a SIEM or enforcement device.  Of course they mention that a more mature organization can derive more from threat intelligence, but they don't devalue starting small either!  Check it out [here](http://podcast.wh1t3rabbit.net/dtr-episode-118-demystifying-threat-intelligence).  The discussion I'm referencing begins at about 15:30 and runs through 21:30.

Threat intelligence is *not an all or nothing proposition.*  Small organizations can, and should, implement a threat intelligence capability scaled to their maturity level.  No one advocates attempting to plop a fully matured infosec program in place on day one.  Why should we take the same approach with threat intelligence?  Let threat intelligence mature on a scale along with an information security program and make it an integral part of those information security operations.

If you're still with me, and you want to start small, I'll outline a few ways to do so in a follow up post in a few days.  I'd love to hear some feedback; you can find me [@swannysec](https://twitter.com/swannysec).
