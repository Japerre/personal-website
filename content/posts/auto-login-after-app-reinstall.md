---
title: "Unveiling iOS Keychain: Simplified Understanding of Automatic Logins"
date: 2024-03-30
draft: false
categories:
  - technical
---

In my quest to bolster my digital privacy, I've found myself uninstalling spyware apps like Reddit and YouTube from my phone, only to reinstall them a few days later (don't judge me 😉) and discovering that I'm seamlessly logged back in. In this blog post, I'll delve into the mechanisms responsible for this phenomenon.

Since HTTP is stateless, every time my device interacts with Reddit, it needs to include a piece of information with its requests to identify me. This crucial piece of data usually comes in the form of an access token appended to the HTTP request via a header:

```Authorization: Bearer <token>```

This token was initially obtained by my device by me typing in my username and password to send to Reddit's authentication server. From that point on, the access token gets stored into local storage on your device. On iphones these tokens are stored into what's called the Keychain. 

From a user's perspective, Keychain functions like any other password manager. When I input my credentials on an app or website using Safari, iOS prompts me to save these details in Keychain, where I can access and manage them in the settings.

However, what's not visible to users are the stored access tokens and similar sensitive data, which are also kept in Keychain. To access this part of Keychain, one would typically need a jailbroken phone or expensive forensics software like [this](https://www.elcomsoft.com/eift.html).

I suspect (though I can't confirm) that when I delete the Reddit app, the access token for Reddit remains untouched in the Keychain. Consequently, upon reinstalling the app, it effortlessly retrieves and employs the existing access token, allowing for automatic login without requiring me to re-enter my credentials. 

It's frustrating that Apple restricts users from exploring their own devices, especially considering that we own and purchase them ourselves. This limitation is one of the reasons why I've decided that when my current iPhone eventually breaks, I won't be replacing it with another iPhone. Instead, I'll opt for an Android phone that supports GrapheneOS, a privacy-respecting operating system that empowers users to customize and control their devices as they see fit.



<!-- 1. could be that Reddit uses Oauth tokens. When you first login to Reddit with your credentials from your phone, you get that token. Now with every request you send that token, so the reddit server knows it's you. It's possible that when you delete the app, this token is not deleted. And when you reinstall the app, the token just gets send with your initial request and you are still signed in. -->



<!-- Apparantly the local keychain from your iphone is stored in /var/Keychains/Keychain-2.db [see this reddit post](https://www.reddit.com/r/ios/comments/wnupiw/is_there_any_way_to_see_everything_whats_stored/) but you need to be jailbroken to access that? 


[nuttige info over keychain op iphone](https://blog.elcomsoft.com/2020/08/extracting-and-decrypting-ios-keychain-physical-logical-and-cloud-options-explored/) -->