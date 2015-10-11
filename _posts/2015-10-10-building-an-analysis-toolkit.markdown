---
published: true
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
|:--------------|:-----------------|
| [FIR](https://github.com/certsocietegenerale/FIR) | Fast Incident Response.  Lightweight IR management platform.  Will track and correlate manually entered IOCs. |
| [SCOT](https://github.com/sandialabs/scot) | Sandia Cyber Omni Tracker.  IR management platform with robust IOC tracking/correlation and plugins for integration with other tools. |
| [RTIR](https://github.com/bestpractical/rtir) | Request Tracker for Incident Response.  Just what it sounds like.  RT with built in workflows for IR. |
| [threat_note](https://github.com/defpoint/threat_note) | Lightweight IoC tracking and enrichment, designed as a research tool. |
| [Microsoft OneNote](https://www.onenote.com/) | Great notetaking app.  Store notebooks locally, or on cloud storage. |
| [Evernote](https://evernote.com/) | Robust cloud based notetaking app with great tagging system.  Take note: No client-side encryption. |
| [Cherrytree](http://www.giuspen.com/cherrytree/) | Simple local note-taking app with an organizational system similar to Evernote. |


**Threat Intelligence/IoC Aggregation and Processing**


|:--------------|:-----------------|
| [CIF](http://csirtgadgets.org/collective-intelligence-framework) | Collective Intelligence Framework.  Collects, aggregates, normalizes, and outputs IoCs in a variety of formats for operationalization.  Can search via API/browser extensions as well.  Self-hosted.  |
| [IntelMQ](https://github.com/certtools/intelmq) | Collects and processes large volumes of threat intelligence from traditional feeds, pastebin, twitter, and more.  Self-hosted. |
| [CriticalStack](https://intel.criticalstack.com/) | Collects and aggregates threat intelligence and outputs to Bro signature files.  Get creative and shape the output to your needs or wait for more output formats. |
| [AlienVault OTX](https://www.alienvault.com/open-threat-exchange) | Open Threat Exchange.  Free web-based threat intel collector/aggregator.  Big focus on information sharing. |
| [ThreatConnect](http://www.threatconnect.com/) | Full threat intel platform.  Enterprise-grade with a nice free feature set ideal for tracking and sharing IoCs individually or in a small team. |
| [MISP](https://github.com/MISP/MISP) | Malware Information Sharing Platform.  Great IoC management platform.  Allows a variety of inputs and outputs and has a robust sharing framework. |
| [CRITS](https://crits.github.io/) | Collaborative Research Into Threats.  Similar concept to MISP, with a bigger focus on analysis. |


**Web-based Research Tools**


|:--------------|:-----------------|
| [PassiveTotal](https://www.passivetotal.org/) | Excellent source of context for malware or IoC analysis.  Whois lookups, passive DNS, SSL cert history, and tie ins with VirusTotal, Domaintools, Alienvault and more.  Good free feature set.   |
| [ThreatCrowd](https://www.threatcrowd.org/) | Great search engine for IoCs complete with visualizations and RSS feeds. Free. |
| [threatRecon](https://threatrecon.co/) | Nice IoC lookup from Wapack Labs.  Free after registration for 1000 searches a month. |
| [malwr](https://malwr.com/) | Online cuckoo malware sandbox analysis.  Free. |
| [VirusTotal](https://www.virustotal.com/) | Does this need a description?  Analysis of files and URLs against known malware signatures and reputation data. |
| [urlQuery](https://urlquery.net/) | URL lookup, provides whois and reputational data as well as running the page load through Snort and Suricata with advanced subscriptions.  |


**Reconnaissance/Context Enrichment**


|:--------------|:-----------------|
| [Automater](https://github.com/1aN0rmus/TekDefense-Automater) | Given a domain or IP, gathers a boatload of useful intel from various web sources.  Lightweight Python script. |
| [Machinae](https://github.com/HurricaneLabs/machinae) | Similar to Automater with more sources of intel, cleaner config, and additional inputs/outputs. |
| [dnstwist](https://github.com/elceef/dnstwist) | Feed it a domain and it will spit out any existing domains that are similar.  Useful when looking for fraud, phishing, or typosquatting. |
| [FOCA](http://blog.elevenpaths.com/2013/12/foca-final-version-ultimate-foca.html) | Windows based recon tool for exploring/mapping domains and finding files, injection opportunities, or other security issues.  Free. |


**Log Analysis/SIEM**


|:--------------|:-----------------|
| [Splunk](https://www.splunk.com/) | Fantastic log analysis tool\SIEM with loads of integrations and flexibility.  Allows for a ton of free-form analysis.  Free to 500 MB/day indexing. |
| [ELK Stack](https://www.elastic.co/products) | Elasticsearch, Logstash, Kibana.  Open source log collector with great visualization via Kibana. |
| [graylog](https://www.graylog.org/) | Slightly easier to setup and use than ELK, has a growing featureset in visualization and plugins.  |


**Visualization/Relationship Research**


|:--------------|:-----------------|
| [Maltego](https://www.paterva.com/web6/products/maltego.php) | Industry standard for this type of work.  Expensive, but decent free feature-set for getting started. |
| [Orange](http://orange.biolab.si/) | Open-source visualization and data analysis. |


**Bonus Items - Random Stuff I Like**


|:--------------|:-----------------|
| [Dashkiosk](https://github.com/vincentbernat/dashkiosk) | Awesome rotating dashboard creator for static displays.  Great for a NOC/SOC.  Chromecast friendly!  |
| [Loki](https://github.com/Neo23x0/Loki) | Scans hosts for presence of a variety of IoCs. |
| [Gavel](https://github.com/brianwarehime/gavel) | Nifty transforms for Maltego that allow an analyst to query traffic records, a lot of human intel possible here. |