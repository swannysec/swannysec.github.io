---
published: false
title: Actor and Campaign Tracking with PassiveTotal
layout: post
tags: [Analysis, Tools, How_To]
image: https://swannysec.net/public/PassiveTotal8.jpg
---
One of the frequent challenges for any analyst is ongoing tracking of a given campaign or actor after initial analysis is completed.  There are a variety of ways to do this, from commercial threat intelligence platforms to manual tracking with spreadsheets.  Add the need to effectively share gathered data quickly and efficiently and you typically have an expensive and/or time consuming endeavor on your hands.  My recent analysis of the [Nebula exploit kit]() saw me using RiskIQ's [PassiveTotal](https://passivetotal.org/) as the primary, nearly exclusive data source.  This left me the opportunity to highlight a couple of awesome features of the PassiveTotal platform that can make the ongoing monitoring, tracking, and sharing of threat data markedly easier.  

What follows will be a short tutorial on the use of the Projects and Monitors features of PassiveTotal.  As you will see, Projects allow you to aggregate related threat data under a public or private project, assign tags to that project, and assign collaborators to facilitate contribution.  Monitors will actively watch for new infrastructure related to the indicators you enable it for, allowing easy addition of new data to a project tracking a given campaign or actor.  These features are available free of charge in limited numbers to registered accounts.

To begin, we'll go ahead and start a new project from the [projects page](https://passivetotal.org/projects):

![PassiveTotal1](https://swannysec.net/public/PassiveTotal1.jpg)

We'll fill it out like so, making it public, adding a name, description, appropriate tags, and assigning a collaborator if necessary:

![PassiveTotal2](https://swannysec.net/public/PassiveTotal2.jpg)

Once the project is up and running, we'll go ahead and add our first indicator, the whois registant e-mail associated with the Nebula EK activity:

![PassiveTotal3](https://swannysec.net/public/PassiveTotal3.jpg)

![PassiveTotal4](https://swannysec.net/public/PassiveTotal4.jpg)

Notice in the previous screenshot that PassiveTotal accepts defanged inputs for indicators; that's super helpful.  If you're ever dealing with a system that does not accept defanged inputs, check out [defang](https://pypi.python.org/pypi/defang), a handy little python package that will defang and re-fang URLs, IPs, and e-mails.

We'll go ahead an add the whois org associated with this activity as well and we're left with this:

![PassiveTotal5](https://swannysec.net/public/PassiveTotal5.jpg)

In order to begin monitoring for new or additional activity associated with this actor, we'll toggle the monitor switches on the right:

![PassiveTotal6](https://swannysec.net/public/PassiveTotal6.jpg)

At this point, any new infrastructure registered using the e-mail or org name we're monitoring will show up under the alerts tab of the project page, and we should also get a handy summary e-mail on a weekly basis showing all of our alert activity, including CSVs:

![PassiveTotal7](https://swannysec.net/public/PassiveTotal7.jpg)

At this point, it's simply a matter of bulk importing your indicators, or adding them as alerts from your monitors fire, and you should have a complete project that you can use to track, share, and collaborate on.  You can view the resulting project here:

https://passivetotal.org/projects/80ab2f3f-e08f-f86a-fade-6f9d3f8a12c6

Hopefully, this will add a simple and free tool to your analysis toolbox.  Thanks to the gang at RiskIQ for providing this excellent service.  As always, I invite comment, debate, or criticism, or other forms of feedback [@swannysec](https://twitter.com/swannysec).
