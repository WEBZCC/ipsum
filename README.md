![Logo](https://i.imgur.com/PyKLAe7.png)

[![License](https://img.shields.io/badge/license-The_Unlicense-red.svg)](https://unlicense.org/)

About
----

**IPsum** is a threat intelligence feed based on 30+ different publicly available [lists](https://github.com/stamparm/maltrail) of suspicious and/or malicious IP addresses. All lists are automatically retrieved and parsed on a daily (24h) basis and the final result is pushed to this repository. List is made of IP addresses together with a total number of (black)list occurrence (for each). Greater the number, lesser the chance of false positive detection and/or dropping in (inbound) monitored traffic. Also, list is sorted from most (problematic) to least occurent IP addresses.

As an example, to get a fresh and ready-to-deploy auto-ban list of "bad IPs" that appear on at least 3 (black)lists you can run:

```
curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1
```

If you want to try it with `ipset`, you can do the following:

```
sudo su
apt -qq install iptables ipset
ipset -q flush ipsum
ipset -q create ipsum hash:net
for ip in $(curl --compressed https://raw.githubusercontent.com/stamparm/ipsum/master/ipsum.txt 2>/dev/null | grep -v "#" | grep -v -E "\s[1-2]$" | cut -f 1); do ipset add ipsum $ip; done
iptables -I INPUT -m set --match-set ipsum src -j DROP
```

In directory [levels](levels) you can find preprocessed raw IP lists based on number of blacklist occurrences (e.g. [levels/3.txt](levels/3.txt) holds IP addresses that can be found on 3 or more blacklists).

Wall of Shame (2021-09-25)
----

|IP|DNS lookup|Number of (black)lists|
|---|---|--:|
209.141.53.166|-|11
141.98.10.179|er.includeswitche.com|11
107.189.3.160|eu.mypanelplus.com|10
107.189.8.8|258223.com|10
60.8.87.190|-|10
205.185.118.82|smtp15.walkertexas.de|10
104.244.79.215|sandbergconsult.dk|10
104.248.193.49|-|10
141.98.10.125|-|10
209.141.32.151|-|10
171.25.193.25|tor-exit5-readme.dfri.se|10
206.189.104.122|-|10
117.248.249.70|-|10
89.234.157.254|marylou.nos-oignons.net|9
107.189.4.119|-|9
199.195.252.247|gre.ligahosting.ro|9
198.98.58.250|-|9
209.141.51.168|soen390.alan.ly|9
205.185.116.145|-|9
198.98.52.69|-|9
221.131.165.40|-|9
45.61.184.15|-|9
221.181.185.94|-|9
107.189.13.122|-|9
222.187.232.60|-|9
185.107.70.202|tor-exit.r3.darknet.dev|9
141.98.10.121|-|9
107.189.31.248|-|9
179.43.141.99|-|9
176.111.173.156|-|9
199.195.248.37|-|9
104.244.74.29|smtp2.geschreitwird.de|9
198.98.53.184|-|9
60.170.247.162|-|9
198.98.51.254|96fa95cd435976cd61.kronossec.net|9
221.131.165.33|-|9
209.141.55.247|-|9
222.187.254.41|-|9
64.113.32.29|tor.t-3.net|9
222.187.232.39|-|9
209.141.55.232|-|9
104.244.75.62|-|9
105.203.195.68|host-105.203.195.68.etisalat.com.eg|9
209.141.52.9|-|9
107.189.30.211|kaufen3.mercedesbenzverwaltung.de|9
45.93.201.148|-|9
185.31.175.220|-|8
89.163.249.244|srv1264.dedicated.server-hosting.expert|8
185.107.47.215|tor-exit.r1.darknet.dev|8
89.163.249.192|srv1116.dedicated.server-hosting.expert|8
185.220.102.243|185-220-102-243.torservers.net|8
162.247.74.74|-|8
199.195.254.38|doktor11.apotheke2021.de|8
164.52.24.164|-|8
205.185.126.99|mail2.cssistgut.store|8
136.144.49.245|-|8
171.25.193.77|tor-exit1-readme.dfri.se|8
171.25.193.78|tor-exit4-readme.dfri.se|8
185.107.47.171|tor-exit.r2.darknet.dev|8
185.220.101.4|berlin01.tor-exit.artikel10.org|8
103.158.147.250|-|8
45.133.1.14|-|8
107.189.1.85|-|8
80.82.77.139|dojo.census.shodan.io|8
178.20.55.16|marcuse-1.nos-oignons.net|8
192.160.102.170|ogopogo.relay.coldhak.com|8
107.189.13.161|-|8
81.161.63.253|-|8
185.220.102.4|communityexit.torservers.net|8
198.98.50.192|-|8
185.130.44.108|tor-exit-se1.privex.cc|8
77.247.181.163|lumumba.torservers.net|8
222.187.227.122|-|8
185.31.175.231|-|8
179.43.175.26|-|8
178.73.215.171|178-73-215-171-static.glesys.net|8
171.25.193.20|tor-exit0-readme.dfri.se|8
107.189.12.48|-|8
213.202.216.189|h176.helix.dedi.server-hosting.expert|8
222.168.30.19|-|8
45.153.160.133|-|8
176.111.173.85|-|8
81.161.63.100|-|8
179.43.176.31|-|8
107.189.30.134|smtp4.achtungumbedingt.de|8
89.163.252.230|ca262.calcit.dedicated.server-hosting.expert|7
185.31.175.228|-|7
185.31.175.226|-|7
80.82.77.33|sky.census.shodan.io|7
148.72.245.63|ip-148-72-245-63.ip.secureserver.net|7
162.247.74.202|djb.tor-exit.calyxinstitute.org|7
162.247.74.206|-|7
162.247.74.204|-|7
139.59.102.170|-|7
5.183.209.217|-|7
221.181.185.198|-|7
71.6.199.23|einstein.census.shodan.io|7
222.186.30.112|-|7
221.181.185.19|-|7
41.33.61.166|host-41.33.61.166.tedata.net|7
45.141.84.126|-|7
188.166.91.169|-|7
161.35.151.232|-|7
185.220.102.244|185-220-102-244.torservers.net|7
185.220.102.242|185-220-102-242.torservers.net|7
185.220.102.248|tor-exit-relay-2.anonymizing-proxy.digitalcourage.de|7
88.9.119.217|217.red-88-9-119.dynamicip.rima-tde.net|7
222.186.42.137|-|7
109.201.133.100||7
209.141.54.139|lv.fc.cx|7
5.2.69.50|-|7
167.99.34.159|-|7
185.220.103.8|mariellefranco.tor-exit.calyxinstitute.org|7
185.220.101.1|berlin01.tor-exit.artikel10.org|7
209.141.34.232|monero.mnpnk.com|7
45.133.1.12|-|7
185.31.175.247|-|7
81.6.43.167|81-6-43-167.init7.net|7
18.27.197.252|wholesomeserver.media.mit.edu|7
185.247.225.55|-|7
5.199.143.202|ca235.calcit.dedicated.server-hosting.expert|7
222.186.42.213|-|7
209.141.54.195|tor1.friendlyexitnode.com|7
162.247.72.199|-|7
221.181.185.140|-|7
45.153.160.129|-|7
185.220.100.253|tor-exit-2.zbau.f3netze.de|7
185.220.100.252|tor-exit-1.zbau.f3netze.de|7
185.220.100.255|tor-exit-4.zbau.f3netze.de|7
185.220.100.254|tor-exit-3.zbau.f3netze.de|7
198.96.155.3|exit.tor.uwaterloo.ca|7
185.31.175.252|-|7
5.104.110.89|ca248.calcit.dedicated.server-hosting.expert|7
185.90.136.69|ksort-fi41-sort.betmam.com|7
185.100.87.72|iclnm.worlpeed.net|7
94.230.208.147|tor3e1.digitale-gesellschaft.ch|7
89.248.167.131|mason.census.shodan.io|7
91.149.225.131|tor-exit-node.miao.pt|7
166.70.207.2|this.is.a.tor.node.xmission.com|7
182.73.123.118|-|7
45.153.160.140|-|7
77.247.181.165|politkovskaja.torservers.net|7
178.62.14.181|-|7
179.43.147.67|mail.alliancestratamanagement.com|7
162.247.74.27|turing.tor-exit.calyxinstitute.org|7
93.174.95.106|battery.census.shodan.io|7
24.224.178.87|host-24-224-178-87.public.eastlink.ca|7
222.186.180.130|-|7
185.220.103.5|chelseamanning.tor-exit.calyxinstitute.org|7
185.31.175.235|-|7
91.219.236.228|441061389-dedicated.serverastra.com|7
45.153.160.2|-|7
209.141.33.39|mail.pomoc-poczta.cloud|7
222.186.42.7|-|7
176.10.104.240|tor1e1.digitale-gesellschaft.ch|7
71.6.146.130|refrigerator.census.shodan.io|7
205.185.121.185|-|7
205.185.125.45|-|7
162.247.74.7|korematsu.tor-exit.calyxinstitute.org|7
185.220.102.253|tor-exit-relay-7.anonymizing-proxy.digitalcourage.de|7
104.244.73.169|luxembourgtor21.lu|7
80.67.172.162|algrothendieck.nos-oignons.net|7
8.209.91.186|-|7
221.131.165.56|-|7
199.195.250.77|ny1.exit.tor.alkyl.eu.org|7
178.20.55.18|marcuse-2.nos-oignons.net|7
222.186.30.76|-|7
104.244.76.13|tor-exit-node.spongebob.nicdex.com|7
89.163.154.91|srv1258.dedicated.server-hosting.expert|7
185.56.80.65|onion.xor.sc|7
45.144.225.143|please.try-to.h4ck.me|7
185.100.87.129|-|7
89.163.252.30|srv1016.dedicated.server-hosting.expert|7
221.181.185.159|-|7
89.163.150.213|ca144.calcit.dedicated.server-hosting.expert|7
185.31.175.207|-|7
185.31.175.215|-|7
221.181.185.151|-|7
176.10.99.200|accessnow.org|7
199.249.230.188|tor99.quintex.com|7
45.153.160.130|-|7
45.153.160.139|-|7
185.247.225.67|-|7
45.133.1.31|-|7
222.186.42.13|-|7
45.238.165.32|45-238-165-32.mhnet.com.br|7
185.129.62.62|tor01.zencurity.dk|7
80.82.70.228|group-ib.ru|7
192.42.116.20|this-is-a-tor-exit-node-hviv120.hviv.nl|7
192.42.116.28|this-is-a-tor-exit-node-hviv128.hviv.nl|7
185.31.175.240|-|7
109.227.63.3|srv-109-227-63-3.static.a1.hr|7
185.220.101.12|berlin01.tor-exit.artikel10.org|7
152.136.18.77|-|7
162.247.73.192|mario-louis-sylvester-lap.tor-exit.calyxinstitute.org|7
185.142.236.35|wine.census.shodan.io|7
192.42.116.16|tor-exit.hartvoorinternetvrijheid.nl|7
124.128.200.114|-|7
221.181.185.135|-|7
209.141.59.180|freedomisnotfree|7
209.127.17.242|-|7
155.4.0.67|h-155-4-0-67.a147.priv.bahnhof.se|7
46.166.139.111|-|7
51.254.143.96|96.ip-51-254-143.eu|7
185.100.87.202|-|7
