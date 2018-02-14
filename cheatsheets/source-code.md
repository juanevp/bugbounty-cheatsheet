## Source code analysis

Download all public source code available for organization under analysis

Search for keywords throughout code:
-API and key. (Get some more endpoints and find API keys.)
-token
-secret
-TODO
-password
-vulnerable
-http:// & https://

Analyze code related to (difficult to get right):
-CSRF
-random
-hash
-MD5, SHA-1, SHA-2, etc.
-HMAC


Search issues for security problems, information shared about infrastructure (search for domains/subdomains)
Look at org. member's projects.

Skim commit history in search of changes related to security.
Check blame and history of files of interest


**Tools**
- [OWASP Static analysis tools](https://www.owasp.org/index.php/Source_Code_Analysis_Tools)
- [NIST Source Code Security Analyzers](https://samate.nist.gov/index.php/Source_Code_Security_Analyzers.html)
- [Awesome static analysis](https://github.com/mre/awesome-static-analysis) (curated list of static analyzers)
- [GithubCloner](https://github.com/mazen160/GithubCloner) (to clone all repositories of the company under analysis)
- [snyk.io](https://snyk.io/test) (check dependencies)
- [Truffle Hog](https://github.com/dxa4481/truffleHog) (search for high entropy strings and secrets in git commit history)
- [git-all-secrets](https://github.com/anshumanbh/git-all-secrets)

**Python**
- [Bandit](https://github.com/openstack/bandit) (static analyzer)
- [Online Requirements Checker](https://pyup.io/tools/requirements-checker/) (check for outdated dependencies)

**Ruby**
- [Brakeman](https://brakemanscanner.org/) (static analyzer)

**JS**
- [LinkFinder](https://github.com/GerbenJavado/LinkFinder)

**.NET**
- [Roslyn Security Guard](https://dotnet-security-guard.github.io/)