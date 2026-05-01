+++
title = "bring your own agent (byoa)"
date = "2026-05-01T00:00:00-05:00"
author = "alex mcculley"
cover = ""
coverCaption = ""
tags = ["ai", "offensive-security", "red-team"]
keywords = ["ai", "claude code", "byoa", "red team", "offensive security", "c2"]
description = "claude code is the new c2"
showFullContent = false
readingTime = false
hideComments = false
color = "" #color from the theme settings
Toc = false
aiDisclaimer = true
+++

> claude code is the new c2.

There's a scene from minority report where Tom Cruise is flying around with a bunch of screens in front of him running an investigation into a precognitive vision trying to identify where a potential murder is taking place. He's issuing commands to a machine by speaking in natural language. It's not that far off to think this may be where cyber attacks are headed. Attacks carried out via Speech To Text (STT) at lightning fast pace.

![minority report](./minority-report.png)

I've been thinking about the implications of AI for attackers and red team operations after reading a post from [embrace the red](https://embracethered.com/blog/posts/2026/agent-commander-your-agent-works-for-me-now/) about an indirect prompt injection based c2 infra. One of the more interesting ideas that I've thought about is with agents you could have an extremely capable operator on endpoints once you have shell access. A viable route might look like:

- install a harness (pi, claude code, etc)
- link to API key, account, etc.
- utilize the agent to continue the attack

Once you have the harness installed and connected, you've got the best tool available to continue your attack. Enumerating the network, probing the endpoint for privilege escalation, and establishing persistence becomes a natural language challenge - not a technical one. With the kind of attack chain I described above, *the agent acts as a post-exploitation toolkit*. It's a BYOA (Bring Your Own Agent) style attack. You can bring over any skills, subagents, and additional tooling you like and craft custom enumeration and (potentially) exploitation in real time on the compromised endpoint. The biggest hurdle is downloading the cli harness, but even that on windows isn't necessarily indicative of compromise or malicious activity in this day and age where everyone is using these tools and claude code in the CLI doesn't even require admin to install. If you get the right workstation, you may not even *need* to do anything other than run `claude` in the CLI. You could even enable `remote control` from the claude code session and run the attacks from your phone. Sure there's some *potential* risk of Anthropic noticing malicious activity but even that isn't a hard stop and easier than you may think to bypass.

For a legitimate Red Team - this kind of attack may not be possible. Clients are (understandably) hesitant to allow for potentially sensitive data flowing to big AI companies. You could utilize a (currently) sub-par self-hosted model (ideally hosted in cloud for ease of connection) to do the same thing but the impact of such an attack may not be realized with a less capable model. But attackers don't care. That's one of the things that makes these things scarier.

For what it's worth, implementing a strong AppLocker policy could prevent this and organizations should most definitely start to monitor the installation of claude code in the CLI as well as creating a chokepoint by implementing an egress proxy for approved AI traffic. It won't stop everything but gives more governance and visibility into AI usage for an organization and even if an attack occurs, you've got a more visible paper trail for IR and forensic analysis. AI is speeding things up exponentially for attackers and defenders. It'll be interesting to see how companies and offensive security firms settle the usage of AI tooling during engagements. Unless that question can be sorted out - there will always be asterisks in engagement reports run without AI. 

## references

- [Agent Commander](https://embracethered.com/blog/posts/2026/agent-commander-your-agent-works-for-me-now/)
