+++
title = "the sodak hackerspace"
date = "2025-11-19T13:24:08-06:00"
author = "alex mcculley"
authorTwitter = "" #do not include @
cover = ""
coverCaption = "collaborate, tinker, learn"
tags = ["hackerspace", "infrastructure"]
keywords = ["", ""]
description = "A brief overview of the SoDak Hackerspace"
showFullContent = false
readingTime = false
hideComments = false
color = "" #color from the theme settings
+++

# overview

My HomeLab has been the biggest boon to my career in IT. It provided me a space to deploy, manage, and experiment with different technologies and also reduce my reliance on big tech companies by self hosting my own services. It's been a lot of fun to build, deploy, break, upgrade, and learn in my own little kingdom so to speak. A while back I was listening to a podcast, I believe it was [Linux Unplugged](https://linuxunplugged.com/) and one of the hosts mentioned that they visited a hackerspace in Berlin. The name alone was enticing but to hear them describe this enclave of technology enthusiasts that meets up and works on projects, learn from each other and have a space to nerd out over things sounded incredible and made me wonder if I could pull something like that off in my own community. 

# goals
There's few ideas that I had going into this endeavour. The first was to provide a space to learn, tinker, and collaborate on projects surrounding the computer space. That's simple enough, people could bring their own workstations and work on their own infra with help from others as needed. But it'd be fun to have some shared infrastructure - a community HomeLab if you will. As I thought about the idea of shared infrastructure there would be levels of logistical organization that would need to be in place, especially if we had a server or two or three that people could hop on. While shared user accounts and just handing out root credentials is easy it's also terrifying and stupid. The only thing is that managing an organization is difficult, complex, and expensive and while the first two will always be the case, I could work hard to make the cost low. Like really low. Then the idea struck:

<center><strong>An entire organization built on top of open source for management and infrastructure.</strong></center>

Built on top of Proxmox, the idea for now as a PoC is to have an all in one management box that you only need to plug into a WAN port on a modem. The entire rest of the infrastructure will be virtualized. Opnsense or Pfsense for the router, headscale for the VPN, FreeIPA for Identity Management, self hosted SSO, Wazuh for SIEM and XDR, managed by ansible, almost everything an organization needs to get off the ground and all while minimizing the reliance on big tech companies. Eventually if it takes off, a template box could be created and shipped to members and everyone could host a node independently and integrate with services as needed (so long as the network connection via headscale is enough).

Of course, as often happens, life has been crazy and my free time went from minimal to zero for quite some time. The idea was always still there though and eventually the opportunity presented itself to launch the [SoDak Hackerspace](https://sodakhacker.space/). The domain was bought, the initial hardware was gathered together, Proxmox installed, and then ... that opportunity fell through. But the dream persisted and progress has happened recently. I write all this to say that I hope one day the SoDak Hackerspace will really start to come together and I get people within my local community involved in it and meetups start happening with projects to work on. If you visit the hackerspace site today, there's not much. Just my profile and I think an initial blog post about the laptop I had started to make into the primary Proxmox node. I did hit a stroke of luck and acquired much better hardware to start with than the laptop so in that sense, we're doing pretty well. I'm hoping to post on the hackerspace blog more often as it gets off the ground starting with a little more detailed writeup of the initial setup.  

Currently Proxmox has been installed, headscale has been configured and working, and there's a pfsense box that has been configured for the internal infrastructure as well a DMZ if deemed necessary. We also have a public xonotic server that can be a bit latent to be honest. My next step is to configure some server templates, get Ansible stood up, and install FreeIPA on a box or two as a way to have identity management. I figured the earlier that gets setup the better so accounts can be created and managed in there. If anybody sees this and has an interest in it feel free to email me at alex@sodakhacker.space or take a look at the website https://sodakhacker.space.
