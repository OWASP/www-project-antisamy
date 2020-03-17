---

title: how_do_i_get_started
displaytext: How do I get started?
layout:  null
tab: true
order: 1
tags: antisamy

---

There are 4 steps in the process of integrating AntiSamy. Each step is detailed in the next section, but the high level overview follows:

1. Download AntiSamy from Maven
2. Choose one of the standard policy files that matches as close to the functionality you need:
* antisamy-tinymce-X.X.X.xml
* antisamy-slashdot-X.X.X.xml
* antisamy-ebay-X.X.X.xml
* antisamy-myspace-X.X.X.xml
* antisamy-anythinggoes-X.X.X.xml
3. Tailor the policy file according to your site's rules
4. Call the API from the code

## Stage 1 - Downloading AntiSamy
First, add the dependency from Maven:

```XML
  <dependency>
    <groupId>org.owasp.antisamy</groupId>
    <projectId>antisamy</projectId>
  </dependency>
```

## Stage 2 - Choosing a base policy file
Chances are that your site's use case for AntiSamy is at least roughly comparable to one of the predefined 
policy files. They each represent a "typical" scenario for allowing users to provide HTML (and possibly CSS) 
formatting information. Let's look into the different policy files:

1) antisamy-slashdot.xml

[Slashdot](https://slashdot.org/) is a techie news site that allows users to respond anonymously to news 
posts with very limited HTML markup. Now, Slashdot is not only one of the coolest sites around, it's also 
one that's been subject to many different successful attacks. Even more unfortunate is the fact that most 
of the attacks led users to the infamous goatse.cx picture (please don't go look it up). The rules for 
Slashdot are fairly strict: users can only submit the following HTML tags and no CSS: `<b>`, `<u>`, `<i>`, 
`<a>`, `<blockquote>`.

Accordingly, we've built a policy file that allows fairly similar functionality. All text-formatting tags 
that operate directly on the font, color or emphasis have been allowed.

2) antisamy-ebay.xml

[eBay](https://www.ebay.com/) is the most popular online auction site in the universe, as far as I can tell. 
It is a public site so anyone is allowed to post listings with rich HTML content. It's not surprising that 
given the attractiveness of eBay as a target that it has been subject to a few complex XSS attacks. Listings 
are allowed to contain much more rich content than, say, Slashdot- so it's attack surface is considerably 
larger. The following tags appear to be accepted by eBay (they don't publish rules): `<a>`, `...`

3) antisamy-myspace.xml

[MySpace](https://myspace.com/) was, at the time this project was born, arguably the most popular social 
networking site. Users were allowed to submit pretty much all HTML and CSS they want - as long as it doesn't 
contain JavaScript. MySpace was using a word blacklist to validate users' HTML, which is why they were subject 
to the infamous Samy worm 
[https://www.vice.com/en_us/article/wnjwb4/the-myspace-worm-that-changed-the-internet-forever]
(https://www.vice.com/en_us/article/wnjwb4/the-myspace-worm-that-changed-the-internet-forever) 
[https://samy.pl/myspace/](https://samy.pl/myspace/). The Samy worm, which used fragmentation attacks combined 
with a word that should have been blacklisted (eval) - was the inspiration for the project.

4) antisamy-anythinggoes.xml

I don't know of a possible use case for this policy file. If you wanted to allow every single valid HTML 
and CSS element (but without JavaScript or blatant CSS-related phishing attacks), you can use this policy 
file. Not even MySpace was _this_ crazy. However, it does serve as a good reference because it contains base 
rules for every element, so you can use it as a knowledge base when using tailoring the other policy files.

## Stage 3 - Tailoring the policy file
Smaller organizations may want to deploy AntiSamy in a default configuration, but it's equally likely that 
a site may want to have strict, business-driven rules for what users can allow. The discussion that decides 
the tailoring should also consider attack surface - which grows in relative proportion to the policy file.

You may also want to enable/modify some "directives", which are basically advanced user options. 
[This page](https://wiki.owasp.org/index.php/AntiSamy_Directive) tells you what the directives are and which 
versions support them.

## Stage 4 - Calling the AntiSamy API
Using AntiSamy is easy. Here is an example of invoking AntiSamy with a policy file:

```Java
import org.owasp.validator.html.*;

Policy policy = Policy.getInstance(POLICY_FILE_LOCATION);

AntiSamy as = new AntiSamy();
CleanResults cr = as.scan(dirtyInput, policy);

MyUserDAO.storeUserProfile(cr.getCleanHTML()); // some custom function
```

There are a few ways to create a Policy object. The `getInstance()` method can take any of the following:
* a String filename
* a File object
* an InputStream

Policy files can also be referenced by filename by passing a second argument to the AntiSamy:scan() 
method as the following examples show:

```Java
AntiSamy as = new AntiSamy();
CleanResults cr = as.scan(dirtyInput, policyFilePath);
```

Finally, policy files can also be referenced by File objects directly in the second parameter:

```Java
AntiSamy as = new AntiSamy();
CleanResults cr = as.scan(dirtyInput, new File(policyFilePath));
```

## Stage 5 - Analyzing CleanResults
The CleanResults object provides a lot of useful stuff.

```Java
getErrorMessages() - a list of String error messages
getCleanHTML() - the clean, safe HTML output
getCleanXMLDocumentFragment() - the clean, safe XMLDocumentFragment which is reflected in getCleanHTML()
getScanTime() - returns the scan time in seconds
```
