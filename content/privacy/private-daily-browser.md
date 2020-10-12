---
title: "Choosing A Browser For Everyday Use"
date: 2020-09-25T16:43:48+02:00

description: ""
categories:
  - "Browser"
  - "Software"
  - "Alternatives"
tags:
  - "Brave"
  - "Firefox"
  - "Google Chrome"

draft: false

# theme-specific params
lead: "Free (and better) alternatives you can try today."
comments: false # Enable Disqus comments for specific page
authorbox: true # Enable authorbox for specific page
pager: true # Enable pager navigation (prev/next) for specific page
toc: true # Enable Table of Contents for specific page
mathjax: false # Enable MathJax for specific page
sidebar: "right" # Enable sidebar (on the right side) per page
widgets: # Enable sidebar widgets in given order per page
  - "taglist"
---

In this article I'm going to choose a browser that fits my needs. The criteria of these browsers will be security, speed and obviously privacy concerns.

## Browsers to avoid

There are some browsers that are outright terrible regarding privacy. There is really no reason to use them considering there are so many better alternatives.
These browsers are:

- Google Chrome
- Chromium
- Microsoft Edge
- Internet Explorer
- Opera
- Vivaldi
- Safari
- Firefox

__Notes:__

- Some people still think that Vivaldi is open source, but in reality it's [not](https://vivaldi.com/blog/vivaldi-browser-open-source/). It probably is the most customizable one on this list, however.

- Opera got bought by a [chinese company](https://www.digitaltrends.com/computing/opera-sold-600-million-chinese-consortium/) and I don't trust any chinese software (Opera is locates in Singapore and thus under chinese law). Also their free VPN is nothing but a proxy. I let the [Terms of Service](https://www.opera.com/terms) speak for itself: __The VPN feature is not an end-to-end service and it does not guarantee that any transmissions of information made while using VPN will be secure.__ Also their [Privacy Statement](https://www.opera.com/privacy) is a very interesting bedtime story.

- Firefox is (in my opinion) on the descending branch, as 250 people got laid off and they made a new deal with Google (read more [here](https://www.techrepublic.com/article/why-mozillas-layoffs-and-google-news-made-me-rethink-my-browser-of-choice/)) so as you can imagine I don't like the way Mozilla has gone in the past few years (the introduction of Pocket was another thing noone asked for and is just a new way of generating more user data). If you like the Firefox look and feel, check out the alternatives below, some are based upon Firefox.

Now that we got this out of the way, lets look at some alternatives and see whay they offer!

## [Brave](https://brave.com/)

Probably the best (or most usable) one on the list. It is based on the open source browser Chromium and developed by a team around Brandon Eich, who created JavaScript and is a Co-Founder of the Mozilla Foundation.

Brave introduced a new way of handling ads. By default, all ads are blocked and the user can volontarily consent to view ads distributed by Braves own ad-network. Some people condemn this business practice as being unethical, since many websites depend on their income from ads. Personally, I don't really care, since I'm blocking all ads anyways, but it might be something you want to consider.

As a "reward" for looking at these Brave-distributed ads, you get BAT, the Basic Attention Token, a cryptocurrency you can exchange against other cryptocurrencies or real money. There was a bit of a controversy about this, since the cryptocurrency gets managed by the platform Uphold, for which you need to state your real name, country, phone number and a photo of you and your ID to sign up, which kinda removes the anonymity aspect. So my recommendation is to just ignore the Brave Rewards (you won't earn that much anyways) and save the fiddling around.

Brave offers synchronization between devices (desktop and mobile), but in my experience it can take some time until the sync starts and its really slow and sometimes it doesn't sync at all. Don't expect an instantanious sync like in Chrome. On the other hand Brave is really fast in providing updates when a new Chromium version gets released, so you have all the new features and security updates.
[A study](https://www.scss.tcd.ie/Doug.Leith/pubs/browser_privacy.pdf) from February 2020 also showed that Brave sends the least telemetry of all browsers and it's the only one that doesn't use identifiers when doing so (you can completely disable telemetry in the settings).

## [Ungoogled-Chromium](https://ungoogled-software.github.io/)

This is the open-source Chromium browser but with out all the Google bits and pieces taken out. This is probably the best browser regarding privacy and security on this list as it doesn't phone home to anyone at all. Despite being a one man project, it is just a few days or weeks behind the newest Chromium version which means you get all the security fixes.

However, since it's just chromium, you can't install addons. Also you need to compile the sourcecode, if there is no package available for your operating system or distribution. Since Chromium is a rather big program (around 200 Mb), it takes a really long time to compile if your PC doesn't have the necessary horsepower.

## [Iridium](https://iridiumbrowser.de)

Another browser based on chromium which also strips out all the Google functionality. Unlike Ungoogled-Chromium, this one is kind of outdated. The latest version for Windows is from April 2020 (as of writing this article) which means it is behind 4 major Chromium updates. The Debian version is even older.
If you don't mind missing some security fixes and a really slow update cycle, then Iridium is for you. Also there are no packages for some Linux distros (like Arch), so your'e also left with compiling the source code.

## [GNU IceCat](https://www.gnu.org/software/gnuzilla/)

IceCat is a fork of Firefox, which strips out all the proprietary software pieces Mozilla uses and adds some addons to it, like HTTPS-Everywhere and LibreJS. It also protects you from fingerprinting and trackers and increases your privacy this way.

However, IceCat is also kind of outdated (the last offical version on their webiste is from June 2019), but there might be never versions in your package manager. Also, if you don't like messing with your JavaScript settings (some sites might be broken) then this browser isn't for you.

## [PaleMoon](https://www.palemoon.org/)

Another fork of Firefox. But this one is based on a way older version of Firefox and has gone its own path since then. The interface isn't really up to date (maybe you don't care about this, but I prefer pretty things to look at) and the codebase is maintained completely by the Palemoon devs.

Palemoon might have some security issues, since the code isn't audited in any way and far away from modern versions of Firefox. In 2019, there has been a [data breach](https://forum.palemoon.org/viewtopic.php?f=17&t=22526) which infected all Windows installers (.exe files) with malware. So always verify your downloads before installing. Also the lead dev, Moonchild, isn't really know for his socially adequate behaviour. On the other hand, it is really lightweight, and might run better on older machines than Chrome of Firefox and it's derivatives.

## [Tor](https://www.torproject.org/)

Tor is the browser which lets you access the "dark web" and it's hidden .onion services. It is also based on Firefox but has stripped out many features. The whole internet traffic gets routed through the Tor network, which means your request will bounce three times between Tor nodes before it reaches its destination. On paper, this increases your privacy and security, since the server doesn't know your real IP address and location, but you have to trust the operators of the Tor nodes to not minitor your traffic, or worse, inject some malware into the request (this only applies to HTTP-connections). [A research](https://kryptera.se/assets/uploads/2016/07/10_honions-sanatinia.pdf) found over 100 suspicious Tor nodes, which snooped on their users or performed man-in-the-middle-attacks.

Another thing to consider is, that Tor is really slow compared to a regular connection since the traffic bounces three times. So if you plan on streaming a lot of videos or downloading many files, you might want to choose another browser. In terms of privacy, Tor is quite good, as long as the exit nodes don't spy on you. Fingerprinting on the other hand is a real issue, since there aren't many people who use Tor, which means you stand out like a glow stick, making it really easy to track and fingerprint you. Another downside is, that some pages don't allow acces via the Tor browser.

If you are planning on using some Tor hidden services, don't be too excited, many sites are broken and there isn't much going on anymore (at least in my experience) and the dark web seems rather empty to me. I don't recommend Tor for everyday use.

## All the other browsers

There are dozens of browsers out there, which promise to do that one thing better than the others. The rule of thumb here is: If you have never heard of them, don't use them. There have been many security issues with these kinds of browsers in the past and there is no real reason to trust the companies who made them (most of them are close-source). For example there have been concerns regarding the [Epic browser](https://medium.com/@xdotc/reasons-not-to-use-epic-privacy-browser-49a42c257791) and the [Comodo browser](https://www.theregister.com/2016/02/02/google_disses_chromodo/) in the past and there is no reason to believe that they have improved in any way. If you want to use a browser that spies on you, just use Google Chrome, this one is at least secure.

## Mobile Browsers

There are only three I can recommend: Brave, Bromite and Firefox Klar. Brave and Bromite are built upon Chromium and offer adblocking by default, however I found Braves to be more consistent. Other than that there isn't much of a difference. If you are using BAT, then obviously Brave is for you.

Firefox Klar on the other hand is made by Mozilla and offers tracking protection out of the box. It has a really weird interface though and I don't get how tabs are suposed to work with this browser, maybe you can figure this out. Sadly, all three don't support addons, which puzzles me, since the regular Firefox mobile browser has built-in addon support.

## In Conclusion

This list and comparison are just my two cents on this topic. There are many more arguments and reasons to use one over the other.

Personally, I use Brave on desktop and mobile without their reward system and I'm really happy with it. Also, in the end, you should use what you feel comfortable with, if you want to use Chrome, just do so. I just wanted to give some insight and alternatives and maybe you decide to switch to another browser anytime soon because you value your online privacy.

Also I'm aware that you should ideally use multiple browsers for different tasks. For example one for online banking, one for signing into different websites (like social media, Amazon, etc.) and a third one for regular browsing and searches. But I don't think this is very suitable for the average user. If I have to do some "sensitive" task like online banking, I close my browser (which is set to clear all my browsing data, cokkies, history, etc.) open it up again and it's like I've never been there. After finishing my task I restart again and resume with my regular work. This takes two seconds and achieves the same as using three browsers.