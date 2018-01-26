---
title: Electrum Critical Vulnerability Exposed
date: 2018-01-08
categories:
- vulnerabilities
tags:
- vulnerabilities
keywords:
- disqus
- google
- gravatar
autoThumbnailImage: false
thumbnailImagePosition: "left"
thumbnailImage: /img/electrum.jpeg
coverImage: /img/bitcoind.jpg
metaAlignment: left
---

On January 6th, Electrum tweeted that there was a critical vulnerability in the versions previous to the Electrum 3.0.4 update.
<!--more-->

See tweet below
{{< image classes="fancybox fig-100" src="/img/electrum_tweet.png" thumbnail="/img/electrum_tweet.png" >}}


Fortunately this bug was updated before any costly exploit. Electrum is the go to wallet for users seeking a fast, light-weight wallet, where you do not have to download the full blockchain. Electrum is also popular among altcoin developers seeking to develop mobile apps.

The [vulnerability](https://bitcointalk.org/index.php?topic=2702103) allowed attackers to steal Bitcoin from users wallets via javascript.

**To exploit this vulnerability,users had to have both:**

- An Electrum Wallet with no password
- Visited a website that executed the javascript exploit code

Electrum has also been criticized for how they handled this as this problem was discovered all the way back to November 24th when a user submitted an [issue on Github](https://github.com/spesmilo/electrum/issues/3374). 

The Electrum wallet was being target for its JSON RPC Vulnerability. The JSON RPC is a protocol which allowed the flow of data between the clients and servers. However this protocol was not secure.

Strange activity was seen as early as Novemeber 24th when attackers were specifically scanning for Electrum wallets which was discovered by [Catalin Cimpanu](https://github.com/spesmilo/electrum/issues/3374)

Even earlier, on November 7th, security researcher [Dimitrios Slamaris](https://twitter.com/dim0x69/status/927967611761188864) noticed attackers scanning for vulnerable Electrum wallets.
with the JSON RPC Vulnerability.
{{< image classes="fancybox fig-100" src="/img/electrum_nov_7.png" thumbnail="/img/electrum_nov_7.png" >}}

Even after all of this attention pointing towards a potential critical Electrum vulnerability, Electrum is yet to send out a patch or discuss the issue.

Finally on January 6th, Google researcher Tavis, Ormandy, discovered this vulnerability and realized that there was an issue on this exact same vulnerability a few months earlier and alerted Electrum again. Finally, they fix the issue and push out a patch. Not very professonal for a company who's reputation relies on its security built in its products.

{{< blockquote "@taviso" "https://twitter.com/taviso/status/949804775473737728" >}}
The bitcoin wallet Electrum allows any website to steal your bitcoins. I was gonna report it...but there was already an open issue from last year. I pointed out this is kinda critical, and they made a new release within a few hours. Update to 3.0.4 if you use it.
{{</ blockquote >}}

Here is the GitHub JSON RPC Vulnerable code being fixed. 

{{< image classes="fancybox fig-100" src="/img/vulnerablecode_electrum.png" thumbnail="/img/vulnerablecode_electrum.png" >}}

To fix the vulnerability the developers removed the code which allowed Cross Origin Resource Sharing(CORS) which was not needed.
A common vulnerability that can happen if you use CORS is if you set 'Access-Control-Allow-Origin" to '*' which allows the application to have access to any resource.


In the image below you can see that the wildcard "*" is set which causes Electrum to be vulnerable.
{{< image classes="fancybox fig-100" src="/img/vulnerable_line.png" thumbnail="/img/vulnerable_line.png" >}}

Thank you for reading and I hope you learned alot.



The image below is a picture of a researcher successfully stealing encryption keys from Electrum through a browser with Javascript
{{< image classes="fancybox fig-100" src="/img/electrum_vuln.png" thumbnail="/img/electrum_vuln.png" >}}


