---
title: "Meltdown and Spectre: Two CPU flaws that affects every processor from 1995 forward"
date: 2018-01-05
categories:
- vulnerabilities
tags:
- exploits
- vulnerabilities
keywords:
- disqus
- google
- gravatar
autoThumbnailImage: false
thumbnailImagePosition: "left"
thumbnailImage: /img/meltdown-spectre-small.jpg
coverImage: /img/meltdown-spectre-large.jpg
metaAlignment: left
---

Initially thought of as cpu "memory leaking", researchers discovered two critical vulnerabilities that have been hidden for over 20 years.
<!--more-->

## What is Meltdown?

Meltdown ([CVE-2017-5754](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5754)) is a CPU vulnerability capable of leaking passwords, encryption keys, messages, pictures, and other sensitive data to an attacker. Meltdown has also been seen to be able to access data outside a virtual machine making it especially critical to cloud computing companies.


Meltdown exploits a vulnerability in Intel CPUs all the way from 1995 called speculative processing and branch prediction.

{{< blockquote "Intel Manual" "https://www.intel.com/content/dam/www/public/us/en/documents/manuals/64-ia-32-architectures-optimization-manual.pdf" >}}
Branch prediction predicts the branch target and enables the processor to begin executing instructions long before the branch true execution path is known.
{{</ blockquote >}}

This "branch prediction" enables processors to predict what programs will do, further increasing system performance and speed. Meltdown works by exploiting an issue where unprivileged code that has kernel permissions. The meltdown attack manual explains how the Meltdown attack works in three steps.

According to the [Meltdown Attack Manual](https://meltdownattack.com/meltdown.pdf),

**Meltdown consists of 3 steps:** 

- Step 1 The content of an attacker-chosen memory location, which is inaccessible to the attacker, is loaded into a register.
- Step 2 A transient instruction accesses a cache line based on the secret content of the register.
- Step 3 The attacker uses Flush+Reload to determine the accessed cache line and hence the secret stored at the chosen memory location.

By repeating these steps for different memory locations, the attacker can dump the kernel memory, including the entire physical memory.
The scary part about Meltdown, is that there are no files or traces. Anti-virus programs cannot stop or detect Meltdown. 


## Is there a fix?

There are currently patches in Linux, Mac OSX, and Windows. Browsers have also updated their software to prevent javascript attacks.

However, there are slowdowns and performance issues after the patches. There are only mitigations. This is most seen on programs that switch between kernel and user modes.
One scary fact about Meltdown is that Microsoft has stopped sending patches to systems using AMD processors as users have reported their systems "not booting" after the patch.


Below is a YouTube video showing the Meltdown exploit in action dumping the memory.

{{% youtube bReA1dvGJ6Y %}}


Below is a YouTube video showing Meltdown spying on passwords

{{% youtube RbHbFkh6eeE %}}

## What is Spectre?

Spectre ([CVE-2017-5753](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2017-5753)) is an exploit on a vulnerability in the physical architecture of the CPU and affects ARM, Intel, and AMD processors. Since the vulnerability is hardware based, there is no ability to patch or update software. 
According to the Spectre Manual, researchers were able to read secrets from memory. 


{{< blockquote "Spectre Manual" "https://spectreattack.com/spectre.pdf" >}}
We created a simple victim
program that contains secret data within its memory
access space. Next, after compiling the victim program
we searched the resulting binary and the operating system’s
shared libraries for instruction sequences that can
be used to leak information from the victim’s address
space. Finally, we wrote an attacker program that exploits
the CPU’s speculative execution feature in order to
execute the previously-found sequences as transient instructions.
Using this technique we were able to read the
entire victim’s memory address space, including the secrets
stored within it.
{{</ blockquote >}}

## Mitigations?

The most likely attack surface for Spectre is through a browser exploit with Javascript. Google reccommends turning on [site isolation](https://support.google.com/chrome/answer/7623121?hl=en-GB) which will keep websites from stealing passwords and data from each other. Although this has been found to increase Chromes memory usage from 10% - 20% which is worth the security enhancements.
Firefox users can also [isolate websites](https://www.ghacks.net/2017/11/22/how-to-enable-first-party-isolation-in-firefox/) to prevent security risks. Additionally, Apple provides [mitigations](https://support.apple.com/en-us/HT208394) for Safari.

This is a big deal, especially since a high profile [Mac Vulnerability](https://x0ex.com/2018/01/mac-os-0-day-kernel-exploit-revealed/) was discovered not even a week  ago.





