---
published: false
title: Linking TorrentLocker to Pony
layout: post
tags: [Analysis, TorrentLocker, Pony]
---
*If you're just here for the IOCs, you will find a link to them at the bottom of the post.*

![](https://swannysec.github.io/public/slenderness/suspiciousdns.jpg)

It all started with a routine glance at some log data.  I noticed a significant uptick in suspicious DNS queries for the subdomain above, thousands dropped by our security gear over the course of six hours or so.  Unfortunately, I have been unable to determine the vector for these because we don't have full PCAP abilities under normal circumstances.  Nevertheless, I was interested in what this subdomain might have been serving up.   What I found initially was not terribly surprising.  What I found when I continued investigating was a huge surprise.  This post will demonstrate how free and open-source intelligence and analysis tools can reveal complex relationships and uncover shared malware infrastructure.

I need to begin with a few caveats:

* I am not a professional analyst.  I am a multi-discipline security engineer responsible for everything from firewall rules, to writing policy, to DFIR.  Analysis is 5% or less of my job and is a hobby.
* Malware reversing is not a strength of mine.  As such, I will not spend a lot of time with the malware discussed in this post.  If you'd like to break it down and make a guest post, please contact me!  Otherwise, please feel free to write it up yourself, I'd love to know more.
* All of the tools used to conduct this analysis are either open-source or free accounts for various services.
* I have omitted some data in the analysis, such as phone numbers.
* The free versions of Maltego and PassiveTotal have significant limitations which mean that the analysis is not fully "fleshed-out."  I will continue to work on this case going forward.

With that said, let's get started!

My first step was to enter the subdomain into [threat_note](https://github.com/defpoint/threat_note), a handy research and indicator tracking notebook from [@brian_warehime](https://twitter.com/brian_warehime).  Threat_note will pull back whois data, passive DNS where possible, and a nice [ThreatCrowd](https://www.threatcrowd.org/ visualization with a quick link to pivot into ThreatCrowd.

![](https://swannysec.github.io/public/slenderness/firstindicator.jpg)

![](https://swannysec.github.io/public/slenderness/firstwhois.jpg)

![](https://swannysec.github.io/public/slenderness/firstviz.jpg)

Not much to see here unfortunately.  Just a subdomain behind a private registrar.  Let's go up a level and look at that root domain.  I dropped it into threat_note as well:

![](https://swannysec.github.io/public/slenderness/rootwhois.jpg)

Still not much new here, but as with the original subdomain, there is some unusual data present.  A Russian registrar located in Nobby Beach, Queensland, Australia?  Certainly bizarre, my interest is now piqued.  Let's scroll down a little further and take a look at the ThreatCrowd visualization.

![](https://swannysec.github.io/public/slenderness/rootviz.jpg)

Now we're cooking!  There are malware hashes, a nice network of subdomains, and an IP all associated with
poytowweryt.com.  In order to understand what we're looking at, understand that ThreatCrowd pulls data from a variety of public intel and analysis sources such as [VirusTotal](https://www.virustotal.com), [malwr](https://malwr.com/), and [Payload Security](https://www.hybrid-analysis.com/) and correlates it with its own history of DNS and whois data.  Data ingested includes domains/subdomains, IPs, malware hashes, and whois information.  Let's hop into [ThreatCrowd](https://www.threatcrowd.org/domain.php?domain=poytowweryt.com) via the handy pivot link provided.

![](https://swannysec.github.io/public/slenderness/firstthreatcrowd.jpg)

![](https://swannysec.github.io/public/slenderness/firstsubdomains.jpg)

A substantial network of subdomains is present, all linked back to a single IP.  How about the malware?

![](https://swannysec.github.io/public/slenderness/firstmalware.jpg)

![](https://swannysec.github.io/public/slenderness/firstmalwr.jpg)

![](https://swannysec.github.io/public/slenderness/HashOneBehaviors.jpg)

![](https://swannysec.github.io/public/slenderness/Slenderness.jpg)

Definitely has some unwanted behavior associated.  And what is Slenderness?  Whatever it is, I stole it as a campaign name for threat_note.  Let's look at [VirusTotal](https://www.virustotal.com/en/file/e1c46cd1b9f9b7e4456ab327c299d41cba30e75cb2f819334e5e6fb65dd5743b/analysis/), what is this thing?  Looks like a fairly standard Crypto-variant ransomware, though some vendors appear to be classifying at a Zeus variant or the Androm Backdoor.  A google search of the IP hosting it, 51.254.140.74 brings us to abuse.ch's [SSL Blacklist](https://sslbl.abuse.ch/intel/cc1c9fc84201246c7150de88f65a0d6f14cc2a78).  Ah, it's TorrentLocker; that will surely ruin someone's day!

![](https://swannysec.github.io/public/slenderness/firstvt1.jpg)
![](https://swannysec.github.io/public/slenderness/firstvt2.jpg)

So what do we have so far?  Looks like a small distribution network for ransomware.  That's a pretty common thing these days, likely a dime a dozen if you're really looking.  Let's hop over to [Maltego](https://www.paterva.com/web6/products/maltego.php) and explore a little more using [ThreatCrowd](http://threatcrowd.blogspot.co.uk/p/threatcrowd-maltego-transform.html) and [PassiveTotal](http://blog.passivetotal.org/passivetotal-maltego-transforms/) transforms.

This is the first domain expanded via the ThreatCrowd transform.  As noted above, I do not have access to the full version of Maltego, so all the subdomains are not present.

![](https://swannysec.github.io/public/slenderness/Maltego1.jpg)

The next step is to enrich the IP using the ThreatCrowd transforms.  These transforms basically extend all the search and correlation power of ThreatCrowd right into Maltego.

![](https://swannysec.github.io/public/slenderness/Maltego2.jpg)

Here we can see the IP hosts the second piece of malware from the main domain as well as a bunch of the subdomains that represent it.  At this point, I want to be sure I've got the full history of the IP, so I elect to transform via PassiveTotal and pull back their entire passive DNS history (sadly I cannot do this for all of the IPs during the investigation due to limitations of the free account).

![](https://swannysec.github.io/public/slenderness/Maltego3.jpg)

The result is a new domain not picked up by ThreatCrowd, highlighted below! The PassiveTotal [results](https://www.passivetotal.org/passive/51.254.140.74) are available below as well.

![](https://swannysec.github.io/public/slenderness/Maltego4.jpg)

 ![](https://swannysec.github.io/public/slenderness/PassiveTotal1.jpg)

Now we've got a new lead.  Enriching itroxitutr.net gives us a new IP and we can see it's hidden behind the same suspicious registrar as before, based on the contact e-mail present.

![](https://swannysec.github.io/public/slenderness/Maltego5.jpg)

Expanding the discovered IP leads us to new malware and two new domains.

![](https://swannysec.github.io/public/slenderness/Maltego6.jpg)

At this stage, I went back to threat_note for some whois data (it can be produced in Maltego too).  Recognize what's circled?  It's that same shady domain registrar.  Aside from the direct DNS associations, there's a very obvious theme present in that all of the domains are registered behind an unusual private registrar.

![](https://swannysec.github.io/public/slenderness/itroxwhois.jpg)

The IP itself, however, gives our second clue in terms of Geolocation (the first being the TLD of the registrar).  It's hosted in Ukraine.  That won't shock anyone in our line of work, but it certainly raises the probability of nefarious intent given the other indications present here.  See below.

![](https://swannysec.github.io/public/slenderness/itroxipwhois.jpg)

What can we learn about the malware related to itroxtutr.net?

![](https://swannysec.github.io/public/slenderness/itroxmalwr1.jpg)

![](https://swannysec.github.io/public/slenderness/itroxmalwr2.jpg)

![](https://swannysec.github.io/public/slenderness/itroxvt1.jpg)

![](https://swannysec.github.io/public/slenderness/itroxvt2.jpg)

Looks like more crypto-variant ransomware, very similar to what was hosted by the original domain, quite likely TorrentLocker again.  At this stage, we've discovered two separate IPs fronted by a good number of domains and subdomains all serving ransomware.  Still nothing out of the ordinary present here, but this is a great exercise nonetheless.

![](https://swannysec.github.io/public/slenderness/maltegopostitrox.jpg)

Expanding and enriching the two new domains lunoxdyv.com and towovker.com brings the following results:

![](https://swannysec.github.io/public/slenderness/Maltego7.jpg)

What do we have here?  More malware and our first actor, that's exciting!  We'll leave Mr. Malkovich alone for a bit and check on the malware.  More ransomware according to VirusTotal:

[0e66f3725446fb6502e91830582452de](https://www.virustotal.com/en/file/3d48318c27d12ee7d3a4699bfac3c3ac42acc18d511862c7ab94e04810c9c21e/analysis/)

[e242fdb77bb2d75bfc29c086ddd4985e](https://www.virustotal.com/en/file/0e68f675c2c2e183ff872b4090ddf73fc45adc5191ae21b60e360a492a7ba4e0/analysis/)

The third file is a zip with the goods inside:

[c8f5cd83c585dee882dc531a29b14e85](https://www.virustotal.com/en/file/5154a59c4626790a7a3fe7221f1bca34d829e3c2d9a1e786f80589e106bdcac4/analysis/)

[78cc33f7f5be12aa7871dd854de1741b](https://www.virustotal.com/en/file/cc6c121899a682d838b93889a4fa4d6c7a7b1523e1cc834dfea287aff2ef08bd/analysis/1445406210/)

Before expanding things any further, here's a look at an overview of what we have discovered so far.  It's reaching a point that it is difficult to take readable screenshots, especially if I use the hierarchical views.  It would appear that these may be two slightly different malware networks sharing a common piece of infrastructure: 93.171.159.109.  Unsurprisingly, that IP is on the SSL Blacklist for being a TorrentLocker C&C host.  There's a nice write-up on TorrentLocker from [@marc_etienne_](https://twitter.com/marc_etienne_) at ESET [here](http://www.welivesecurity.com/wp-content/uploads/2014/12/torrent_locker.pdf).

![](https://swannysec.github.io/public/slenderness/Maltego10.jpg)

We want to continue following the breadcrumbs, so let's go back to Mr. Malkovich.  What can we find out by pivoting off his address via ThreatCrowd?

![](https://swannysec.github.io/public/slenderness/Maltego8.jpg)

We're not in Kansas anymore, Toto!  That makes two new domains.  Expanding those domains reveals yet more malware and a shared host, 191.1.156.96.

![](https://swannysec.github.io/public/slenderness/Maltego9.jpg)

What kind of malware is Mr. Malkovich serving up at motohex.net and hexdroid.net?  More ransomware?  Looks like it.

[09e54636eb4de5e782cc19a9b7dcf267](https://www.virustotal.com/en/file/68971172e5d1cf5d82776280f67218ba0cf233731e583dfde342afa7ee25ccdd/analysis/)

[98ac006fdb0880711509a51ab4901eec](https://www.virustotal.com/en/file/18440e1faa8186e153e8fe175cdc1c971dceec20e38d92fc8fdbfe9bc7f310e5/analysis/)

[ebacb76eb45d6800da6f4f074ae24e61](https://www.virustotal.com/en/file/1b7e194848522c4bee4a870ef4f74c5b8cec030cb3f61ce60f55db8d67f14fb8/analysis/)

[e9923215f43335260ad445ebf9375035](https://malwr.com/analysis/YmQ3ZmIyYTE1MGYyNGMzNDkxZDJiYmJlMGJkODg0YmY/)

[2e902e458d88cea396a9cf73068db07d](https://www.virustotal.com/en/file/b230f30fd26be4a879d8bdf4504ecf3e374c25ac2bd2880b1342a35284a80d8d/analysis/)

Sure enough, it's [TorrentLocker](https://sslbl.abuse.ch/intel/3df43035b3d1c665d55a334e41c5bcd3a6a5fc67/) again!  Taking a look in threat_note for the whois records of these domains brings something very interesting:

![](https://swannysec.github.io/public/slenderness/motorhexwhois.jpg)

![](https://swannysec.github.io/public/slenderness/hexdroidwhois.jpg)

A name to go with that e-mail!  Sergey Yashin, perhaps a play on a retired ice hockey [player](https://en.wikipedia.org/wiki/Sergei_Yashin).  Though a likely alias, let's pull the whois in Maltego and draw a link between Sergey and his e-mail.  I'll revisit Sergey in another post.

![](https://swannysec.github.io/public/slenderness/Yashin1.jpg)

From here, I expanded the malware hashes and checked for other communication.  False positives have been removed, such as communication to Windows Update.  Looks like everything communicates with 194.1.156.96:

![](https://swannysec.github.io/public/slenderness/motornet.jpg)

Let's do a whois via Maltego and expand 194.1.156.96.  At this point, I have to apologize because the relationships start to become so tangled that it's difficult to work in Maltego and display things in a way that's organized:

![](https://swannysec.github.io/public/slenderness/leavingransomware.jpg)

So, now we have three more domains and a new actor, Alexey Morozov (I omitted the listed phone number).  In addition, the IP is not owned by Sergey Yashin as I had expected.  How strange!  Alexey is a malware author, as seen [here](https://www.virustotal.com/en/file/28a07f8c8deaf19268b21cd1af381e91c5028dbc547c49c1037957b1cd469f67/analysis/) on the file detail tab.  It's also possible he's really an attempt at registering as another hockey [player](https://en.wikipedia.org/wiki/Alexei_Morozov).  Sad to see retired hockey players need to supplement their income in this manner (obviously, again, these are likely aliases).

Once we expand wsevgocis.com and hosiroxair.net, we find a familiar sight, the same anomalous private registrar from our earliest findings:

![](https://swannysec.github.io/public/slenderness/194expanded.jpg)

At this point, we're still in a network that appears to be dedicated to the distribution of ransomware, primarily, if not entirely TorrentLocker.  That's about to change.  Let's expand madfortgoes.ru.  Just one link, to a piece of malware, and no useful whois information.  Is this a dead end?

![](https://swannysec.github.io/public/slenderness/madfortmalware.jpg)

Investigating the malware brings about substantially more [nefarious](https://www.virustotal.com/en/file/b1378cc0168beefd7b7891cbd58d5282e9d33fd6c159464d6f728d46797ba76a/analysis/) than TorrentLocker.

![](https://swannysec.github.io/public/slenderness/firstponylink.jpg)

It looks like we finally have our first link to something more than ransomware.  If we assume the commenter (a regular commenter on VT https://www.virustotal.com/en/user/kingxyz/ ) is correct, we've clearly left pure TorrentLocker network.  On top of that, it's dropped by [Pony/Fareit](https://www.virustotal.com/en/file/90857805c139b3acea91fe38a49db3a50281d2f9e6f1f3af63770736225f44be/analysis/).  Let's expand that potential bot:

![](https://swannysec.github.io/public/slenderness/betabot.jpg)

There's a lot to process here.  I begin by expanding the IPs first (I left the whois details out as they do not appear to be relevant):

![](https://swannysec.github.io/public/slenderness/betaexpandips.jpg)

The IP's don't reveal any complex relationships so I began digging through the domains.  Rearmheadfire.com is the only domain with  whois data and additional links outside this network, as seen below:

![](https://swannysec.github.io/public/slenderness/betabotexpandeddomains.jpg)

At last, this is where we hit our first undeniable links to the Pony botnet after the mention from the VT comment above.  [Damballa](https://www.damballa.com/) has a fantastic write-up available [here](https://www.damballa.com/wp-content/uploads/2015/08/Damballa_PonyUp.pdf).  Contained within is the following:

![](https://swannysec.github.io/public/slenderness/damballavaleryy.jpg)

![](https://swannysec.github.io/public/slenderness/damballaponyip.jpg)

Well hello!  Looks like a clear link indeed from our rinky-dink TorrentLocker network to the Pony botnet!

Here's what the final view looks like in two different formats:

![](https://swannysec.github.io/public/slenderness/finaloverview.jpg)

![](https://swannysec.github.io/public/slenderness/finaloverview1.jpg)

This is by no means the end of this network, but this post is long enough.  I am continuing to investigate and my current view looks something like this:

![](https://swannysec.github.io/public/slenderness/continuingwork.jpg)

What conclusions can we draw from this analysis?  First and perhaps foremost, open source and free tools can be tremendously powerful.  Beyond my own hardware, I didn't pay a dime for any of this data or the tools to analyze it.  The result is pretty interesting; I managed to uncover, in the span of an evening, a link from an operating TorrentLocker distribution network to the Pony botnet.  Second, this analysis reveals that malware infrastructure sharing and reuse is likely prevalent among Eastern European cybercriminal groups.  As I continue to analyze this case, I'm curious to see if there will be links to additional malware distribution networks.  Finally, and perhaps unsurprisingly, these cybercriminals are making heavy use of private registrars and false whois data to shield both themselves and their infrastructure.

I welcome any comments or additional analysis!  Find me over at [@swannysec](https://twitter.com/swannysec).

The IOCs generated by this investigation are hosted on [github](https://github.com/swannysec/slenderness-torrentlocker-pony-network).  For now, a Maltego Entity file is all that's available.  As soon as I can get my hands on a full version of Maltego I will add CSVs (CSV export is disabled in the free version).  IOCs will be updated as I progress through additional analysis.



Credits:

* Brian Warehime for inspiration and [threat_note](https://github.com/defpoint/threat_note/).
* Christian P. and his excellent [blog](http://www.cyintanalysis.com/) for giving me the confidence to tackle analysis and providing some "blueprints."
* Chris Doman for [ThreatCrowd](https://www.threatcrowd.org/).
* [PassiveTotal](https://www.passivetotal.org/), [malwr](https://malwr.com), [Virustotal](https://www.virustotal.com/), and [Paterva Maltego](https://www.paterva.com/web6/products/maltego.php).