# Certspotter

```zsh
curl https://certspotter.com/api/v0/certs\?domain\=example.com | jq '.[].dns_names[]' | sed 's/\"//g' | sed 's/\*\.//g' | uniq
```

```zsh
curl https://certspotter.com/api/v0/certs\?domain\=example.com | jq '.[].dns_names[]' | sed 's/\"//g' | sed 's/\*\.//g' | uniq | dig +short -f - | uniq | nmap -T5 -Pn -sS -i - -p 80,443,21,22,8080,8081,8443 --open -n -oG -
```

# Sublist3r One-liner

This runs [Sublist3r](https://github.com/aboul3la/Sublist3r) on a list of domains and outputs the results in separate files.

```
. <(cat domains | xargs -n1 -i{} python sublist3r.py -d {} -o {}.txt)
```

# [Apktool](https://ibotpeaches.github.io/Apktool/) to [LinkFinder](https://github.com/GerbenJavado/LinkFinder)

```
apktool d app.apk; cd app;mkdir collection; find . -name \*.smali -exec sh -c "cp {} collection/\$(head /dev/urandom | md5 | cut -d' ' -f1).smali" \;; linkfinder -i 'collection/*.smali' -o cli
```

# [Aquatone](https://github.com/michenriksen/aquatone/) One-liner

```
$ echo "aquatone-discover -d \$1 && aquatone-scan -d \$1 --ports huge && aquatone-takeover -d \$1 && aquatone-gather -d \$1" >> aqua.sh && chmod +x aqua.sh
$./aqua.sh domain.com
```

# [relative-url-extractor](https://github.com/jobertabma/relative-url-extractor)

```
$ ruby extract.rb demo-file.js
$ ruby extract.rb https://hackerone.com/some-file.js
$ ruby extract.rb '|cat demo-file.js' -c
```

**Subdomain scraping**
- [Sublist3r](https://github.com/aboul3la/Sublist3r)
- [enumall](https://github.com/jhaddix/domain)
- [BruteSubs](https://github.com/anshumanbh/brutesubs)
- https://dnsdumpster.com (DNS and subdomain recon)
- [SubBrute](https://github.com/TheRook/subbrute)

**Subdomain bruteforcing**
- [MassDns](https://github.com/blechschmidt/massdns)
- [GoBuster](https://github.com/OJ/gobuster)
- [Knock](https://github.com/guelfoweb/knock)

**Portscanning**
- [Masscan](https://github.com/robertdavidgraham/masscan)

**Visual identification**
- [EyeWitness](https://github.com/ChrisTruncer/EyeWitness)

**Platform indentification (fingerprinting)**
- [Wappalyzer](https://www.wappalyzer.com/)
- [Built With](https://builtwith.com/)
- [WhatWeb](https://github.com/urbanadventurer/whatweb)
- [WAFW00F (WAF fingerprinting)](https://github.com/EnableSecurity/wafw00f)

**Vulneratibily identification**
- [Vulners - vulnerability database](https://vulners.com/landing)
- [CWE (Common Weakness Enumeration)](https://cwe.mitre.org/index.html)
- [NVD (NIST National Vulnerability Database)](https://nvd.nist.gov/)
- [Retire.js](https://github.com/RetireJS/retire.js)
- [Findsploit](https://github.com/1N3/Findsploit)
- [Nikto](https://cirt.net/Nikto2)

**Content/Attack-surface discovery - Directory bruteforcing**
- [Intrigue](https://github.com/intrigueio/intrigue-core)
- [GoBuster](https://github.com/OJ/gobuster)
- [Robots disallowed](https://github.com/danielmiessler/RobotsDisallowed)

**Reconnaissance misc.**
- [Reverse IP Lookup](http://reverseip.domaintools.com/) (Domainmonitor)
- [Security headers](https://securityheaders.io/) (Security Report, missing headers)
- https://mxtoolbox.com (wide range of DNS-related recon tools)
- https://publicwww.com/ (Source Code Search Engine)
- http://ipv4info.com/ (Find domains in the IP block owned by a Company/Organization)
- [HackerTarget Tools](https://hackertarget.com/ip-tools/) (DNS recon, site lookup, and scanning tools)
- [VirusTotal](https://virustotal.com/en-gb/domain/google.com/information/) (WHOIS, DNS, and subdomain recon)
- [crt.sh](https://crt.sh/?q=%25.uber.com) (SSL certificate search)
- [Google CT](https://transparencyreport.google.com/https/certificates) (SSL certificate transparency search)
- [PenTest Tools](https://pentest-tools.com/information-gathering/google-hacking) (Google dorks)
- [Gitrob](https://github.com/michenriksen/gitrob)

**Recon helper services**
- [Wayback machine](https://archive.org/web/) (Find stuff which was hosted on the domain in past)
- [Censys](https://censys.io/)
- [Shodan](https://www.shodan.io/)
- http://threatcrowd.org (WHOIS, DNS, email, and subdomain recon)
