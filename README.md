# GoAltdns
[![License](https://img.shields.io/badge/license-MIT-_red.svg)](https://opensource.org/licenses/MIT)
[![Go Report Card](https://goreportcard.com/badge/github.com/subfinder/goaltdns)](https://goreportcard.com/report/github.com/subfinder/goaltdns) 
[![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/subfinder/goaltdns/issues)

GoAltdns is a permutation generation tool that can take a list of subdomains, permute them using a wordlist, insert indexes, numbers, dashes and increase your chance of finding that estoeric subdomain that no-one found during bug-bounty or pentest. It uses a number of techniques to accomplish this. It can allow for discovery of subdomains that conform to patterns. GoAltdns takes in words that could be present in subdomains under a domain (such as test, dev, staging) as well as takes in a list of subdomains that you know of.

The tool itself is very simple and is built with golang concurrency providing it very quick execution times. 

# Installation Instructions

The installation is easy. Just `go get` the repo.

```bash
go get github.com/subfinder/goaltdns
```

Note - You need to copy the words.txt file into the same directory as the tool or specify it's location via the -w flag.

## Upgrading
If you wish to upgrade the package you can use:

```bash
go get -u github.com/subfinder/goaltdns
```

# Usage

GoAltdns can read hosts directly from standard input, or either take a single host as argument, or a list of hosts. To provide a single host, you can use the `-h` option. In order to provide a list of hosts, you can use the `-l` option.

Sample run:

```bash
ice3man@TheDaemon:~/tmp/goaltdns$ ./altdns -host phabricator.freelancer.com
1phabricator.freelancer.com
phabricator1.freelancer.com
10phabricator.freelancer.com
1-phabricator.freelancer.com
phabricator10.freelancer.com
phabricator-0.freelancer.com
1.phabricator.freelancer.com
...
```

Sample run reading from stdin:

```bash
ice3man@TheDaemon:~/tmp/goaltdns$ echo phabricator.freelancer.com | ./altdns 
1phabricator.freelancer.com
phabricator1.freelancer.com
10phabricator.freelancer.com
1-phabricator.freelancer.com
phabricator10.freelancer.com
phabricator-0.freelancer.com
1.phabricator.freelancer.com
...
```

You can pass custom wordlists using the -w option. Currently, it uses words.txt taken from [here](https://github.com/haccer/altdns/blob/master/words.txt).

By default, goaltdns writes to the standard output. If you want to save the results to a file, you can use `-o` flag with the name of then file to write to it.

```bash
ice3man@TheDaemon:~/tmp/goaltdns$ ./altdns -l ~/uberinternal -o output.txt
```

This will render a blank console but the tool will still write to the output file.

# License

GoAltdns is made with 🖤 by [Subfinder](https://github.com/subfinder) team.

See the **License** file for more details.

# Thanks

GoAltdns is heavily inspired from original [altdns](https://github.com/infosec-au/altdns) by @infosec_au and @nnwakelam. Thanks to them and their awesome research. Also, the wordlist is taken from [haccer](https://github.com/haccer/)
