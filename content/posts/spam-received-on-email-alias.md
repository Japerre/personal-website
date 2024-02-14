+++
title = 'Spam Received on Email Alias'
date = 2026-07-30T01:05:27+02:00
draft = false
categories = ['Tech I Use']
tags = ['trivia']
+++

If you've read a few of my previous posts, you've probably noticed that I'm a big fan of **SimpleLogin**. It allows you to create a unique email alias for every online account, so you never have to hand out your real email address.

Besides the obvious privacy benefits, there's another advantage that people often mention: if a company suffers a data breach or decides to sell your email address, you'll know exactly who leaked it. Since every service gets its own unique alias, any spam sent to that alias immediately tells you where your address came from.

I've been using SimpleLogin for over two years now and have accumulated more than 150 aliases.

![](/images/spam-received-on-email-alias/simplelogin_number_of_aliases.png)

Until recently, I had never actually seen this happen in practice.

Then I received this email.

![](/images/spam-received-on-email-alias/spam-email.png)

Notice that it was sent to the following alias:

**[kennel_surgical427@simplelogin.com](mailto:kennel_surgical427@simplelogin.com)**

That alias was only ever used for a single account, so I immediately knew where to start looking.

Out of curiosity, I checked the address on Have I Been Pwned, and sure enough, it showed up in the data breach of the technology news site *Wired*.

![](/images/spam-received-on-email-alias/have-i-been-pwned.png)

So after more than two years of using email aliases, I finally got to experience one of their biggest advantages firsthand.

It's a small thing, but it's surprisingly satisfying to know exactly **which** service leaked your email address instead of having to wonder where the spam came from.

In this case, all I had to do was disable that single alias. No need to change my real email address, no need to update dozens of accounts, and no impact on any of my other services.

Moments like this are exactly why I'll keep using email aliases for every account I create.
