---

title: related_projects
displaytext: Related Projects
layout:  null
tab: true
order: 2
tags: antisamy

---

The following ports of AntiSamy are known to exist:

## Grails
Daniel Bower created a [Grails plugin](https://github.com/danieldbower/grails-sanitizer) for AntiSamy. No updates since 2015 however.

2 related projects built on top of the OWASP ESAPI for Java library (which uses AntiSamy for Java under the hood) are:

* [grails-xss-sanitizer](https://github.com/rpalcolea/grails-xss-sanitizer) - This supports Grails 3 and is a port of the following:
* [XssSanitizer](https://github.com/tonyzampogna/XssSanitizer) - Supports Grails 2

## .NET
A new (2020+) .NET port of AntiSamy is available at the
[OWASP AntiSamy .NET project](https://github.com/spassarop/antisamy-dotnet/). This version of AntiSamy is looking for a
few good developers to help make it feature-synchronized with the Java version.

If it doesn't suit your needs, consider 
[Microsoft's AntiXSS library](https://archive.codeplex.com/?p=wpl). However, this library is now end 
of life too. Microsoft states: "In .NET 4.0 a version of AntiXSS was included in the framework and 
could be enabled via configuration. In ASP.NET v5 a white list based encoder will be the only encoder."

## Python
A port of AntiSamy to Python was attempted, but has been abandoned since 2010. Michael Coates suggests 
you check out project [Bleach instead](https://pypi.org/project/bleach/).

## PHP
Although a PHP version was initially planned, we now suggest
[HTMLPurifier](http://htmlpurifier.org/) for safe rich input validation for PHP applications.

