---

layout: col-sidebar
title: OWASP AntiSamy
site_side: true
tags: antisamy
level: 3
type: tool
pitch: AntiSamy is a Java component that can sanitize HTML/CSS to eliminate potentially malicious JavaScript.

---
<!-- rebuild 40 -->

[![OWASP incubator](https://img.shields.io/badge/owasp-incubator%20project-blue)](https://www2.owasp.org/projects#div-incubator)

## OWASP AntiSamy

AntiSamy was originally authored by Arshan Dabirsiaghi (arshan.dabirsiaghi [at] gmail.com) of Contrast Security with help from Jason Li (jason.li [at] owasp.org) of Aspect Security and is currently maintained by Dave Wichers (dave.wichers [at] owasp.org).

### Description
The OWASP AntiSamy project is a few things. Technically, it is an API for ensuring user-supplied HTML/CSS is in compliance within an application's rules. Another way of saying that could be: It's an API that helps you make sure that clients don't supply malicious cargo code in the HTML they supply for their profile, comments, etc., that get persisted on the server. The term "malicious code" in regards to web applications usually means "JavaScript." Cascading Stylesheets are only considered malicious when they invoke the JavaScript engine. However, there are many situations where "normal" HTML and CSS can be used in a malicious manner. So we take care of that too.

Philosophically, AntiSamy is a departure from contemporary security mechanisms. Generally, the security mechanism and user have a communication that is virtually one way, for good reason. Letting the potential attacker know details about the validation is considered unwise as it allows the attacker to "learn" and "recon" the mechanism for weaknesses. These types of information leaks can also hurt in ways you don't expect. A login mechanism that tells the user, "Username invalid" leaks the fact that a user by that name does not exist. A user could use a dictionary or phone book or both to remotely come up with a list of valid usernames. Using this information, an attacker could launch a brute force attack or massive account lock denial-of-service. We get that.

Unfortunately, that's just not very usable in this situation. Typical Internet users are largely pretty bad when it comes to writing HTML/CSS, so where do they get their HTML from? Usually they copy it from somewhere out on the web. Simply rejecting their input without any clue as to why is jolting and annoying. Annoyed users go somewhere else to do their social networking.

The OWASP licensing policy (further explained in the membership FAQ) allows OWASP projects to be released under any approved open source license. Under these guidelines, AntiSamy is distributed under a BSD license.

### What is AntiSamy
OWASP AntiSamy provides:

This page shows a big-picture comparison between the versions. Since it's an unfunded open source project, the ports can't be expected to mirror functionality exactly. If there's something a port is missing -- let us know, and we'll try to accommodate, or write a patch!

### Presentations
From OWASP & WASC AppSec U.S. 2007 Conference (San Jose, CA): AntiSamy - [Picking a Fight with XSS (ppt)](http://www.owasp.org/images/e/e9/OWASP-WASCAppSec2007SanJose_AntiSamy.ppt) - by Arshan Dabirsiaghi - AntiSamy project lead

From OWASP AppSec Europe 2008 (Ghent, Belgium): [The OWASP AntiSamy project (ppt)](http://www.owasp.org/images/4/47/AppSecEU08-AntiSamy.ppt) - by Jason Li - AntiSamy project contributor

From OWASP AppSec India 2008 (Delhi, India): [Validating Rich User Content (ppt)](https://www.owasp.org/images/9/9d/AppSecIN08-ValidatingRichUserContent.ppt) - by Jason Li - AntiSamy project contributor

From Shmoocon 2009 (Washington, DC): AntiSamy - [Picking a Fight with XSS (pptx)](https://slideplayer.com/slide/4360528/) - by Arshan Dabirsiaghi - AntiSamy project lead

### News and Events
[28 Sep 2017] Please update AntiSamy to 1.5.7 or later per CVE-2017-14735 and CVE-2016-10006

