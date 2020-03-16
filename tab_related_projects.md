---
title: Related_Projects
displaytext: Related Projects
layout:  null
tab: true
order: 3
tags: antisamy
---

The following ports of AntiSamy are known to exist:

## Grails
Daniel Bower created a [Grails plugin](https://www.grails.org/plugin/sanitizer) for AntiSamy.

## .NET
A .NET port of AntiSamy is available at the [OWASP AntiSamy .NET page](https://wiki.owasp.org/index.php/Category:OWASP_AntiSamy_Project_.NET). The project was funded by a Summer of Code 2008 grant and was developed by Jerry Hoff. However, this version of AntiSamy has not been updated in a while, and is looking for a few good developers to help make it feature-synchronized with the Java version. 

If it doesn't suit your needs, consider [Microsoft's AntiXSS library](https://archive.codeplex.com/?p=wpl). However, this library is now end of life too. Microsoft states: "In .NET 4.0 a version of AntiXSS was included in the framework and could be enabled via configuration. In ASP.NET v5 a white list based encoder will be the only encoder."

## Python
A port of AntiSamy to Python was attempted, but has been abandoned since 2010. Michael Coates suggests you check out project [Bleach instead](https://pypi.org/project/bleach/)

## PHP
Although a PHP version was initially planned, but we now suggest [HTMLPurifier](http://htmlpurifier.org/) for safe rich input validation for PHP applications.

