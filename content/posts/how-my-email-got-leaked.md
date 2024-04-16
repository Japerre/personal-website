---
title: "How I almost got scammed trough Spearphising"
date: 2024-04-15
# draft: true
categories:
  - Tech I Use 
tags:
  - phishing
  - cybersecurity
---


I recently received a series of emails from what appeared to be Porkbun, the DNS provider for my domain japerre.xyz, urging me to renew my premium plan.

![](/images/how-my-email-got-leaked/emails.png)
![](/images/how-my-email-got-leaked/email_example.png)


At first glance, these emails seemed harmless enough. However, they landed in my spam folder, which was the first red flag that something might be off.

Suspicion set in... Was Porkbun compromised? How else did these scammers obtain my email? Then it struck me that I don’t use my personal email with Porkbun and these scammers got my email simply because well... I gave it to them by having it in the footer of my blog 🤦‍♂️. 

Here’s likely how the scammers targeted me:
- ***Email Harvesting***: They scanned my site and found my email address embedded in a mailto link.
- ***DNS Provider Lookup***: By performing a WHOIS DNS search for japerre.xyz, they identified my DNS provider.

Armed with this information, they crafted a spearphishing attack tailored just for me pretending to be Porkbun. I must admit, the deceptive emails were alarmingly convincing; had they not been filtered into my spam folder, I might have been enticed to click on a link. The sole giveaway was the discrepancy between the trusted display name, "Porkbun.com" and the actual sender's email, "info&#64;sa-vermorel.fr". This is a classic case of email spoofing. Fortunately, current email security protocols are robust enough to mark these malicious emails as spam. This incident was quite an eye-opener, even for someone who prides themselves to be internet savvy and not vulnerable to phishing attacks. It highlighted that constant vigilance is essential.

To prevent future risks, I've now switched my contact email to contact@japerre.xyz.

Setting up my own email domain @japerre.xyz was suprisinlgy straightforward with SimpleLogin. It then lets you easily create an unlimted amount of email aliases that all forward to your personal email address. The benefit of this is two-fold:
1. Any email sent to contact@japerre.xyz indicates the sender connected with me through my website.
2. It keeps my personal email address private and undisclosed online

Once again, my experience with [SimpleLogin](https://simplelogin.io/) has left me a very satisfied customer! 