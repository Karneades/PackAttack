# PackAtt&ck - List attacks against software packages

PackAtt&ck is a list of various package manager attacks using two commons
attacks: typosquatting and dependency confusion.

> The attack does not exploit a new technical vulnerability, it rather tries to
> trick people into installing packages that they not intended to run on their
> systems.

By using typosquatting attackers use similar named (typosquatted) packages to
distribute malicious packages and with dependency confusion attackers take
advantage of malicious package placed in public repositories which are then
installed due to higher priority of these package repositories.

The attacks are possible to the nature of community repositories used to
provide an easy way for publishing and installing packages. 

Common package managers are for example PyPi for Python, rubygems.org for
Ruby, npmjs.com for Node.js and Javascript and the PowerShell Gallery
(PSGallery) for PowerShell.

The topic is well-known and a lot of research was done in this area. Here some
references to mention a few: [pytosquatting project and awesome research by Benjamin Bach and Hanno Böck from 2016/2017](https://pytosquatting.overtag.dk/), [write-up about this attack vector against programming language package managers](http://incolumitas.com/2016/06/08/typosquatting-package-managers/), another [awesome and in-depth blog post about that topic](http://incolumitas.com/2016/06/08/typosquatting-package-managers/) and after the npm typosquatting incident in 2017 [Chester Burbidge made further research about the problem of typosquatted packages](https://blog.scottlogic.com/2018/02/27/hunting-typosquatters-on-npm.html). 

## Collection of attacks

In **August 2017** an [incident occurred regarding the npm package
cross-env](https://twitter.com/kentcdodds/status/892372685048627200). The name
`crossenv` (without the dash) was used to steal information from users. 
> it looks like this npm package is stealing env variables on install, using
> your cross-env package as bait

The same [user which uploaded the typosquatted cross-env packages also
published several other
packages](https://twitter.com/iamakulov/status/892485192883073024). [The
administrators of npmjs wrote an article about the incident](https://blog.npmjs.org/post/163723642530/crossenv-malware-on-the-npm-registry.)

> On August 1, a user notified us via Twitter that a package with a name very
> similar to the popular cross-env package was sending environment variables
> from its installation context out to npm.hacktask.net. We investigated this
> report immediately and took action to remove the package. Further
> investigation led us to remove about 40 packages in total.

Further [in-depth research was made and
published](https://blog.scottlogic.com/2018/02/27/hunting-typosquatters-on-npm.html)
and [different](https://www.theregister.co.uk/2017/08/02/typosquatting_npm/)
[articles](https://medium.com/@liran.tal/fighting-npm-typosquatting-attacks-and-naming-rules-for-npm-modules-a0b7a86344aa)
[wrote](https://thenewstack.io/npm-cleans-typosquatting-malware/)
[about](https://threatpost.com/attackers-use-typo-squatting-to-steal-npm-credentials/127235/)
the incident.

In **September 2017** the `urllib3` package targeted by using the package named `urllib`.

> Protect yourself from Python typosquatting attacks with pipsec
> https://www.pytosquatting.org/  #supplychain #attack #Python

https://twitter.com/x0rz/status/910057711391399938

> SK-CSIRT identified malicious software libraries in the official Python
> package repository, PyPI, posing as well known libraries. A prominent example
> is a fake package urllib-1.21.1.tar.gz, based upon a well known package
> urllib3-1.21.1.tar.gz.

See good write up by the SK-CSIRT at http://www.nbu.gov.sk/skcsirt-sa-20170909-pypi/.

A [thorough write up after the notification of malicious packages by the PyPI
administrators is found on the mailing
list](https://mail.python.org/pipermail/security-announce/2017-September/000000.html).

[Other](https://thenewstack.io/python-package-repository-struggles-deal-typosquatting/) [articles](https://nakedsecurity.sophos.com/2017/09/19/pypi-python-repository-hit-by-typosquatting-sneak-attack/) [writing](https://arstechnica.com/information-technology/2017/09/devs-unknowingly-use-malicious-modules-put-into-official-python-repository) [about](https://www.golem.de/news/pypi-boesartige-python-pakete-entdeckt-1709-130098.html) [the](https://www.reddit.com/r/netsec/comments/4n4w2h/taking_over_17000_hosts_by_typosquatting_package/) [incident](https://www.bleepingcomputer.com/news/security/ten-malicious-libraries-found-on-pypi-python-package-index/).

In **2019**, there was a typo package for `dateutil` in PyPI ([Github issue](https://github.com/dateutil/dateutil/issues/984))

> There is a fake version of this package called python3-dateutil on PyPI that contains additional imports of the jeIlyfish package (itself a fake version of the jellyfish package, that first L is an I). That package in turn contains malicious code starting at line 313 in jeIlyfish/_jellyfish.py

In **April 2020**, _The Hacker News_ published a story about [Over 700 Malicious Typosquatted Libraries Found On RubyGems Repository](https://thehackernews.com/2020/04/rubygem-typosquatting-malware.html), citation from the blog post:

> As developers increasingly embrace off-the-shelf software components 
into their apps and services, threat actors are abusing open-source 
repositories such as RubyGems to distribute malicious packages, intended
 to compromise their computers or backdoor software projects they work 
on.
>
>In the latest research shared with The Hacker News, cybersecurity experts at ReversingLabs revealed over 700 malicious gems
 — packages written in Ruby programming language — that supply chain 
attackers were caught recently distributing through the RubyGems 
repository.

In **October 2021**, a typo package for `mitmproxy` was in PyPI which includes an RCE ([Tweet](https://twitter.com/maximilianhils/status/1447525552370458625), [article on bleepingcomputer](https://www.bleepingcomputer.com/news/security/pypi-removes-mitmproxy2-over-code-execution-concerns/)).

> Copycat package could trick devs into falling for 'newer' version

Further articles from October 2021 about typosquatting NPM packages: [NPM packages disguised as Roblox API code caught carrying ransomware [possible prank, but packages have multiple downloads]](https://www.theregister.com/2021/10/27/npm_roblox_ransomware/) and [Newly Found npm Malware Mines Cryptocurrency on Windows, Linux, macOS Devices](https://blog.sonatype.com/newly-found-npm-malware-mines-cryptocurrency-on-windows-linux-macos-devices).

> The two poisoned libraries – `noblox.js-proxy` and `noblox.js-proxies` – were typosquatting (named to be confusingly similar to) noblox.js, a Roblox game API wrapper available on NPM and as a standalone download.

On **23rd March 2022** JFrog published an article about a [Large-scale npm attack targets Azure developers with malicious packages](https://jfrog.com/blog/large-scale-npm-attack-targets-azure-developers-with-malicious-packages/).
> The attacker seemed to target all npm developers that use any of the packages under the @azure scope, with a typosquatting attack. In addition to the @azure scope, a few packages from the following scopes were also targeted –  @azure-rest, @azure-tests, @azure-tools and @cadl-lang.

> Since this set of legitimate packages is downloaded tens of millions of times each week, there is a high chance that some developers will be successfully fooled by the typosquatting attack.

In **January 2023**, [PyTorch discloses malicious dependency chain compromise over holidays](https://www.bleepingcomputer.com/news/security/pytorch-discloses-malicious-dependency-chain-compromise-over-holidays/)

> PyTorch has identified a malicious dependency with the same name as the framework's `torchtriton` library. This has led to a successful compromise via the dependency confusion attack vector.

> The malicious `torchtriton` dependency on PyPI shares name with the official library published on the PyTorch-nightly's repo. But, when fetching dependencies in the Python ecosystem, PyPI normally takes precedence, causing the malicious package to get pulled on your machine instead of PyTorch's legitimate one.

This type of supply chain attack is known as "dependency confusion," as [first reported](https://www.bleepingcomputer.com/news/security/researcher-hacks-over-35-tech-firms-in-novel-supply-chain-attack/) by BleepingComputer in 2021, just as the attack vector was popularized by ethical hacker Alex Birsan.

## Defense against typosquatting and dependency confusion

Detect typosquatted packages by using scripts and use levenshtein distance or generated list of package names to search for malicious packages and report abuse.

Different package managers also search for typosquatted packages (when
uploading new packages) because the problem is well known, e.g. new package
with a name from a already uploaded packages with just a number at the end.

Reserve dummy package to prevent typosquatting and dependency confusion
because you are in control of these package names.

## Related projects

* [https://incolumitas.com/2016/06/08/typosquatting-package-managers/](https://incolumitas.com/2016/06/08/typosquatting-package-managers/)
* [https://pytosquatting.overtag.dk/](https://pytosquatting.overtag.dk/)
* [http://www.nbu.gov.sk/skcsirt-sa-20170909-pypi/](http://www.nbu.gov.sk/skcsirt-sa-20170909-pypi/)
* [https://github.com/benjaoming/pytosquatting](https://github.com/benjaoming/pytosquatting)
* [https://blog.scottlogic.com/2018/02/27/hunting-typosquatters-on-npm.html](https://blog.scottlogic.com/2018/02/27/hunting-typosquatters-on-npm.html)
* [https://www.npmjs.com/package/check-typosquatters](https://www.npmjs.com/package/check-typosquatters)
* [https://github.com/chestercodes/RepoHunt](https://github.com/chestercodes/RepoHunt)
* [https://github.com/Karneades/psyposquatter](https://github.com/Karneades/psyposquatter)
