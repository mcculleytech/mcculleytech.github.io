+++
title = "pjpt"
date = "2025-03-21T21:13:47-05:00"
author = "alex mcculley"
authorTwitter = "" #do not include @
cover = "img/pjpt_logo.webp"
coverCaption = ""
categories = ["certifications", "offensive-security", "penetration-testing"]
tags = ["pjpt", "tcm"]
description = "review of tcm's practical junior penetration tester exam"
showFullContent = false
readingTime = false
hideComments = false
color = "" #color from the theme settings
+++

# overview
Last year I focused on acquiring my 1st Offensive security certification. I chose the PJPT (Practical Junior Penetration Tester) because I had taken some training from TCM a while back and thought it was good material, and the cost was easy to justify. I managed to get the certification the second attempt (more on that later). Overall found the experience to be a good one, and recommend it for beginners. I really like the hands on keyboard style of examination and found this to be a great entry level exam for someone like myself who's done some amount of network penetration testing, but wanted to take a low stakes level exam to get used to the format and the formal report writing.

# training
The PEH (Practical Ethical Hacking) course was a really good penetration testing Active Directory basics course. I actually took an earlier version of the course through Udemy years ago, and found some things to be the same, but many parts were updated as they should have been. If you go on the TCM discord( which I did infrequently, but did from time to time), you'll often hear that the PEH is all you'll need to pass the PJPT. That is an entirely accurate statement from my experience. My one gripe with the training was the report writing section. I felt that it was lacking in the necessary information to actually write a report that would allow you to pass the PJPT in the 1st attempt.

# exam experience
I took my exam on a Thursday to start so I'd be done with the exam by Monday. You're given 2 days with machines, and two days to write the report & submit for grading. I found the lab environment to be quite stable, and only really having to reset for a minor issue once, which was cleared up right way. I went into the exam with a methodology ready and used an obsidian vault to take my notes. I followed my methodology which led me to domain compromise within about 8 hours. I think I could have got DA quicker, but I was treating this like a real engagement and trying to find all the possible vulnerabilities and exploit them. Honestly I had fun during my time in the actual environment and I liked that you could use any tools you wanted to bring. I had taken a Red Team training through my work before this exam and played with some really nice tools like [CredNinja](https://github.com/Raikia/CredNinja), [ADExplorerSnapshot.py](https://github.com/c3c/ADExplorerSnapshot.py), and the Windows-based offensive security box [CommandoVM](https://github.com/mandiant/commando-vm) and liked that I could bring whatever I wanted to the exam.

# report writing
Here's the pain point. Maybe it's my inexperience in writing formal reports, maybe it's TCM's training, maybe its the report template TCM provides. whatever it was, it took me 2 days to do it. Admittedly I made a silly mistake in my first submission, but when I asked for clarification for my 2nd submission I did not get any clarity on what exactly I should include. So I took my time and threw in everything that I had. So. Many. Screenshots. About halfway through, I thought to myself there's got to be a way to automate this process. If-had to do this frequently I'd probably try to template it out in Obsidian, or work on some other 'markdown automation. The report writing and submission was not fun, but a tedious slog. I guess that's the price you pay for getting to do really cool work. Once I finished the second writeup, I was proud of all the work and information I put into the report and was happy to have it graded in ~5 hours.

