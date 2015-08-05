---
.main-title

# Drupal Heists

#### github.com/bjeavons/drupal-heists

---
.image .target

<cite>https://www.flickr.com/photos/roadsidepictures/2923629922</cite>

% 110MM records lost, cost $162MM

---
.quote

>Had the company’s security team responded when it was supposed to, the theft ... [affecting] as many as one in three American consumers, ... never would have happened at all.
<cite>http://www.bloomberg.com/bw/articles/2014-03-13/target-missed-alarms-in-epic-hack-of-credit-card-data
</cite>

% 6 months earlier installed, $1.6MM detection tools, 24/7 team spotted but officials did nothing

---

## Ben Jeavons

* work at CARD.com
* Drupal Security Team
* coltrane on Drupal.org
* @benswords on Twitter

---
.image .imagetext .hackers

## agenda

* how you got hacked
* why the hack
* what to do about it

% goal take some mystery out of hacks, give overview of proactive & reactive, forensics & tools

---
.testpattern

% begin with a story, its a tragedy

---
.disclaimer

The following is based on actual events. Only the names, locations and events have been changed.

% this and other examples actually happened

---
.image .hero

% meet our hero

---

### workin' on your website

% here is our hero, working on the website

---
.image .php

% writing code

---
.image .files

% managing the server

---

### stumbles upon something odd

% out of the ordinary

---
.image .filesshell

% next to index.php

---
.image .shell

% feeling worried

---
.image .shellbrowser

% feeling scared

---

## it’s a php shell

% scared

---
.image .scared

---
.quote

>"The script is a backdoor, capable of downloading + injecting + installing new binaries/processes into the system."
<cite>actual developer who found shell</cite>

---
.image .imagetext .hacked

### you've been hacked

---
.image .over

% told you it was a tragedy

---
.image .imagetext .everyone

## everyone gets hacked

---
.image .biggest

<cite>http://www.informationisbeautiful.net/visualizations/worlds-biggest-data-breaches-hacks/</cite>

% target, anthem, sony, jpmorgan chase, apple, sony again, nytimes, OPM, & not just the big companies

---
.quote

>The 2012 Data Breach Investigations Study by Verizon shows that in 855 data breaches they examined, 71 percent occurred in businesses with fewer than 100 employees."
<cite>http://www.forbes.com/sites/cherylsnappconner/2013/09/14/are-you-prepared-71-of-cyber-attacks-hit-small-business/
</cite>

---
.image .drupalorg

---
.image .pwned

% side note

---
.image .wordpress

---
.image .imagetext .hackers

## hackers

---

## why the hack?

* money & private data
* damage reputation
* make a statement & lulz

% "Internal employees, business partners, and collusion threats make up less than 10 percent of overall data thieves" - verizon study

---

## how you were hacked

% get back to our story

---
.image .shell

---

## ask questions

* when was the shell accessed?
* what was it used for?
* how did it get installed?
* what else happened?

---
.image .log

% webservers record visitor access

---
.text

grep “content-in.php” access_log

% we can look for access to the shell

---

* "GET /content-in.php HTTP/1.1" 200 427
* "GET /content-in.php HTTP/1.1" 200 427
* "GET /content-in.php HTTP/1.1" 200 427
* "POST /content-in.php HTTP/1.1" 200 329

%

---

* how did it get installed?
* what else happened?

---
.text

grep “140.211.10.16” access_log

% access logs have IP address

---

* "GET /content-in.php HTTP/1.1" 200 427
* "GET /phpmyadmin/index.php HTTP/1.0" 200
* "POST /phpmyadmin/tbl_replace.php HTTP/1.0" 200
* "POST /user HTTP/1.0" 302
* "GET /user/1 HTTP/1.0" 200

% see all traffic from that IP address

---
.image .phpmyadmin

---
.image .imagetext .skype

#### root and empty pass gets into phpmyadmin
#### OMFGBBQSAUCE

---

* "GET /phpmyadmin/index.php HTTP/1.0" 200
* "POST /phpmyadmin/tbl_replace.php HTTP/1.0" 200
* "POST /user HTTP/1.0" 302
* "GET /user/1 HTTP/1.0" 200

---
.image .facepalm

---

### what we know

* found PhpMyAdmin with no password
* attacker read user database table
* attacker logged into Drupal
* used Drupal’s PHP filter to install PHP shell

% before how to deal with it

---
.image .over

---

## other ways you were hacked

---
.text

running out-of-date software

w/ known vulnerabilities

% attacker just reads changelogs, ubercart xss to change payment URL, flash vulnerability

---
.image .neighborhood

% whole neighborhood, shared hosting, settings.php

---
.image .drupalgeddon

---
.image .sa05

% sa05 was a big deal, probably the worse, 7 years since last

---
.image .hackers

% pause, we were hacked, found out why, could we have prevented?

---
.image .imagetext .ironman

### secure yourself

% lion and the gazelle

---

## quicklist

* run up-to-date software
* secure account access
* secure default config
* SFTP/SSH & HTTPS
* educate your team
* (theres lots more to do)

---

## stay up-to-date

* be aware of updates
* review and & apply updates
* use version control
* use config management

---

## stay up-to-date

* @drupalsecurity
* RSS feed & mailing list
* core's update notifier
* do this for all software

---

## test & apply

* version control
* config management
* continuous integration

---

## secure accounts

* strong passwords
* two-factor authentication
* audit user roles & permissions

% audit contractors, educate users

---

### strong passwords

* lastpass / 1password
* password policy / password strength

% rotate system passwords

---

## plan for the worst

% do all those proactive things, and more, but also plan for being hacked

---

### incident response

* discovery
* containment
* preserve evidence
* restore service
* documentation
* reporting
* forensics
* drupalize.me/node/1974

---
.image .hackers

---

## recap

* everyone gets hacked
* stay up to date
* use strong passwords
* secure default config
* plan for the worst

---

## links

* Your site got hacked, now what?
 * drupal.org/node/2365547
* Incident response blog post
 * drupalize.me/node/1974
* Writing secure code
 * drupal.org/writing-secure-code

---

## thanks

* slide text
 * Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)
 * http://creativecommons.org/licenses/by-sa/4.0/
