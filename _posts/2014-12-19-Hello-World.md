---
layout: post
title: CVE-2014-0343
---
I discovered my first vulnerability late last year, to a router. That allowed attacker to escalation their privileges from a basic user, with no ability to change any settings, to admin of the router allowing full control.



Virtual Access Router GW6110A
 US-CERT Report: VU#213046

I discovered this by simply looking through the HTML of the web interface. What I saw was a JavaScript script being used to control access level. And the way in which this was controlled was with a JavaScript variable (integer value) set to the appropriate level, and then using a simple if statement to check if admin or not. With the correct admin level right there in plain text. So to escalated my privilege to admin, I simply went into a web developer console, chrome in my case, then simply changed the variable to that of admin level. Then clicking on the admin panel I was given access, as before it prompted me for a admin password. This is commonly known as, "External Control of Assumed-Immutable Web Parameter" which basically allows an attacker to edit web parameters for example cookies, hidden fields, and in this case JS variables.

More on these type of attacks.

I surprised at how easy this attack was, it seemed like a basic web hacking challenge. But then I considered that this is a common theme with router web interfaces, poor security. I don't think the impact is huge in this case but it demonstrates a couple of larger security issues. One being that router security is often full of security holes especially with web interfaces, default passwords, and improper implementations of security features. Two since these interfaces are rarely explored in depth except for setup and maintenance or admins choose consoles over interfaces, that security holes can be easily overlooked. These issues are also magnified with products that don't have a large market share.

I would just like to say the vendor, Virtual Access, was very quick with a response to the issue. Also would like to thank the team at US-CERT in helping me disclose the vulnerability in a efficient and ethical manner.
