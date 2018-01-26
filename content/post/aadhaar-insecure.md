---
title: India ID Verification Company is running insecure code in Android application
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
thumbnailImage: /img/fsociety.jpg
coverImage: /img/bank_account_link.png
metaAlignment: left
---
On Twitter, a security researcher who goes by the name [Elliot Anderson](https://twitter.com/fs0c131y) revealed that Aadhaar was using insecure code and the company was saving personal user details including pictures in a local database with a hard coded password.
<!--more-->

Aadhaar is a company who develops special identification numbers for each Indian citizen to verify their identity and save personal details. For example, with Aadhaar you are able to connect your bank account with you Aadhaar id number. Aadhaar boasts over 1 Billion people being subscribed to the service and has 99% of people who are 18 and older in India registered.

Although Aadhaar has been successful in India, there have been increasing privacy and surveillance concerns about how they are using the data and how securely they are storing it.

In a post by twitter user, @fs0c131y, he revealed that Aadhaar was storing their user's personal information with a simple password and insecure seed opening up potential risks for customers.


Elliot shared that the seed was a basic string of "123456789" and the database password was hardcoded as "db_password_123". The image of the insecure code is below.

{{< image classes="fancybox fig-100" src="/img/insecure-data-aadhaar.png" thumbnail="/img/insecure-data-aadhaar.png" >}}

aadhaar_insecurecode_2.png
Further testing the vulnerabilities of the Aadhaar app, Elliot discovered that even after the app was restarted multiple times that the database password remained the same. 

**In the insecure local database, the developers stored**

- Biometric Data - Picture
- Date of Birth
- Aadhaar ID
- User ID
- Address
- Name


{{< image classes="fancybox fig-100" src="/img/aadhaar_insecurecode_2.png" thumbnail="/img/aadhaar_insecurecode_2.png" >}}

Although these insecure programming practices might seem like a big deal, a flaw was discovered in Aahaards SMS system where you could find out someones banking information by just knowing their Aadhaar id number.

**The procedure followed these steps**

- 1. Dial *99*99*1# from your phone
- 2. You will see a box appear on the screen asking you to enter you Aadhaar Id number
- 3. A confirmation screen
- 4. Displays if a bank account has been linked to the id and if it has, it will display the bank account holder's name


By using someone elses Aadhaar number, attackers can find where an individual is banking at and what the name of the account is. This insecure flaws and lack of authentication could be leveraged by attackers, marketers, and spam bots.

References

[HindustanTimes](http://www.hindustantimes.com/tech/flaw-in-uidai-s-sms-service-lets-anyone-with-your-aadhaar-number-trace-your-bank-info/story-dT0NdHkkjs3mS492hqbTcN.html)

[@fs0s13ty](https://twitter.com/fs0c131y/status/951409241780314114)


