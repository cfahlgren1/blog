---
title: Qubes OS is offering additional protection for its systems from Meltdown through "fully virtualized" VMs
date: 2018-01-11
categories:
- vulnerabilities
tags:
- vulnerabilities
- patches
keywords:
- disqus
- google
- gravatar
autoThumbnailImage: false
thumbnailImagePosition: "left"
thumbnailImage: /img/qubes-logo-icon-name-slogan-fb.png
coverImage: /img/xfce-fresh-installed.png
metaAlignment: left
---

The Qubes OS [new security pack](https://github.com/QubesOS/qubes-secpack/blob/master/QSBs/qsb-037-2018.txt#L32) mentions that "fully virtualized" VMs provide significant security for Meltdown attacks.
<!--more-->

The fully virtualized VMs are in effect in Qubes OS version 3.2 forward. Qubes OS 4.0 offers full virtualization across all Virtual Machines (VM). However, they still rely on para virtualized (PV) based subdomains which could be vulnerable to leaking information with Meltdown.
For users still on Qubes OS 3.2, Qubes plans to release an update that will switch all the VMs to run in fully-virtualized mode. 
Qubes also notes that Meltdown affects only virtual machines that are running parralel to the 
attacking VM. The Meltdown cannot attack shutdown VMs because these are almost immediately allocated to other VMs thus wiping the memory.

In the Qubes Security Pack they mention,

{{< blockquote "Intel Manual" "https://www.intel.com/content/dam/www/public/us/en/documents/manuals/64-ia-32-architectures-optimization-manual.pdf" >}}
... almost all the VMs in Qubes 4.0 are
fully-virtualized by default (specifically, they are HVMs), which
mitigates the most severe issue, Meltdown.
{{</ blockquote >}}

**However, Qubes is offering other provisions to further protect your systems.**

- In Qubes OS 4.0, the use of Disposable VMs is an additional remedy for further protecting your system. The Disposable VMs can now be used for networking and usbs which further increases the security.
- Seeming how important encryption and screen locker passwords have seen to be vulnerable to Meltdown, Qubes offers additional protection by using the Qubes Split GPG which would allow the user to keep encryption keys and passwords in an isolated VM that is shut down most of the time. 

Qubes also notes that attackers must have physical access to the computer to make use of encryption keys and screenlocker passphrase.

**Qubes has four options to follow if you believe you have been affected by Meltdown**

- Change your screen locker password

- Change your encryption passphrases, specifically (LUKS) disk encryption

- Re-encrypt your disks and files to force the change of encryption key (make sure to backup and reinstall data)

- Evaluate odds of your PGP, SSH, or TLS keys being compromised and generate new secrets

Sources

[Qubes Security Pack](https://github.com/QubesOS/qubes-secpack/blob/master/QSBs/qsb-037-2018.txt#L164)
