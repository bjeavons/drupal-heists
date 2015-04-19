---
.main-title

# Drupal Heists
### Security Stories & Practical Plans

---
.image .target

<cite>https://www.flickr.com/photos/roadsidepictures/2923629922</cite>

---
.quote

>Had the company’s security team responded when it was supposed to, the theft ... [affecting] as many as one in three American consumers, ... never would have happened at all.
<cite>http://www.bloomberg.com/bw/articles/2014-03-13/target-missed-alarms-in-epic-hack-of-credit-card-data
</cite>

---
.image .imagetext .hackers

## agenda

* hackers gonna hack
* why they hack
* what you do about it

---

## Ben Jeavons

* work at CARD.com
* Drupal Security Team
* coltrane on Drupal.org
* @benswords on Twitter

---

## story time

% all of the following based on real stories

---

## you're working on your website

---
.image .php

% writing code

---
.image .files

% managing the server

---

### you stumble upon something odd

% out of the ordinary

---
.image .filesshell

---
.image .shell

% feeling worried

---
.image .shellbrowser

% feeling worse

---

## it’s a php shell

% scared

---
.image .imagetext .hacked

### you’ve been hacked

---

## everyone gets hacked

---
.image .biggest

% target, anthem, sony, jpmorgan chase, apple, sony again, nytimes

---
.quote

>The 2012 Data Breach Investigations Study by Verizon shows that in 855 data breaches they examined, 71 percent occurred in businesses with fewer than 100 employees."
<cite>http://www.forbes.com/sites/cherylsnappconner/2013/09/14/are-you-prepared-71-of-cyber-attacks-hit-small-business/
</cite>

---
.image .drupalorg

---
.image .wordpress

---
.image .imagetext .hackers

## hackers

---

## why the hack?

* money
* steal private data
* damage reputation
* espionage
* lulz

% "Internal employees, business partners, and collusion threats make up less than 10 percent of overall data thieves"

---

## how you were hacked

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

---
.text

grep “content-in.php” access_log

---

* "GET /content-in.php HTTP/1.1" 200 427
* "GET /content-in.php HTTP/1.1" 200 427
* "GET /content-in.php HTTP/1.1" 200 427
* "POST /content-in.php HTTP/1.1" 200 329

---

## ask questions

* how did it get installed?
* what else happened?

---
.text

grep “140.211.10.16” access_log

---

* "GET /phpmyadmin/index.php HTTP/1.0" 200
* "POST /phpmyadmin/tbl_replace.php HTTP/1.0" 200
* "POST /user HTTP/1.0" 302
* "GET /user/1 HTTP/1.0" 200

---
.image .phpmyadmin

---
.image .skype

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

### what we know

* found PhpMyAdmin with no password
* attacker read user database table
* attacker logged into Drupal
* used Drupal’s PHP filter to install PHP shell

---
.quote

>"The script is a backdoor, capable of downloading + injecting + installing new binaries/processes into the system."

---

## other ways you were hacked

---
.text

running out-of-date software

w/ known vulnerabilities

% ubercart xss to change payment URL

---
.text

3rd party plugin that writes files

% flash vuln

---
.text

shared hosting

% read settings.php

---
.image .sa05

% sa05 was a big deal, probably the worse
% but 7 years

---
.image .hackers

% pause

---
.image .imagetext .hackers

### stay ahead of the pack

% lion and the gazelle

---

## quicklist

* run up-to-date software
* secure account access
* secure default config
* SFTP/SSH & HTTPS
* (theres lots more to do)

---

## stay up-to-date

* be aware of updates
* review and & apply updates
* use version control
* use config management

---

### secure account access

* strong passwords
* two-factor authentication
* audit user roles & permissions

---

## plan for the worst

---

### incident response

* discovery
* containment
* preserve evidence
* restore service
* documentation
* reporting
* forensics

% lets apply this to how we got hacked

---
.image .imagetext .files

## discovery

% we stumbled upon the php shell

---

### preserve evidence

* server image
* db & code backups
* logs

---

## documentation

* have a lot to communicate
* there are legal implications

---

## reporting

* internal & external
* leadership
* legal implications
* be careful about external messaging

% watch out for links in emails

---

## links

* Your site got hacked, now what?
 * drupal.org/node/2365547
* Incident response blog post
 * lb.cm/incident
* Writing secure code
 * drupal.org/writing-secure-code

---

## credits & thanks

* Joe Shindelar
 * https://drupalize.me/blog/201501/being-prepared-when-everything-goes-wrong
* Michael Hess and Greg Knaddison
 * ideas, feedback, and support
* slide text
 * Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)
 * http://creativecommons.org/licenses/by-sa/4.0/
