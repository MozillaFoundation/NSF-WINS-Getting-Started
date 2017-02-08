# NSF-WINS-Getting-Started

The following is a list of (largely open-source) technologies, tools and projects that may be helpful to teams participating in the [NSF WINS challenges](http://wirelesschallenge.mozilla.org) as they are getting started on their projects. Huge thanks to [Josh King](https://github.com/jheretic) for compiling the initial list. Suggestions and/or additions are most welcome--please either send a pull request or [create a new issue](https://github.com/MozillaFoundation/NSF-WINS-Getting-Started/issues) with a description of your suggestion.

## Routing Daemons ##

Routing daemons are largely split into two categories, link-state and distance-vector, though the widely used BATMAN algorithm is more of a hybrid that uses a form of "ant routing"):

* [OLSRd:](http://www.olsr.org/mediawiki/index.php/Main_Page) Optimized Link State Routing. One of the first major open-source mesh routing projects still in use, the OLSR.org implementation of IETF RFC3626 started as a graduate student thesis project and was widely used in early community networks. Due to its shortcomings and bugs, BATMAN was created and replaced it on some networks, but it was simultaneously adopted by Funkfeuer (see below) and updated to be competitive with other protocols. High-performance but high-overhead, it has a lot of cross-platform support and is still maintained, but will likely be phased out in favor of OLSR2.

* [OLSR2:](http://www.olsr.org/mediawiki/index.php/Main_Page) The new successor to OLSR, OLSR2 is based on RFCs 7181 and 6130. Vastly simplified and optimized from v1, it's based on an extremely well-engineered software framework.

* [Babel:](https://www.irif.fr/~jch/software/babel/) A high-performance distance vector protocol. More widely used in networks outside of Europe, it's not really a part of the same community. It's a mandatory component of the IETF Homenet initiative for self-configuring in-home networks. Works very well with low overhead and limited configuration.

* [batmand:](https://www.open-mesh.org/projects/batmand/wiki) The original implementation of the Better Approach to Mobile Ad-hoc Networking algorithm, batmand is no longer used but is still maintained in stasis by the original designer of the algorithm.

* [batman-adv:](https://www.open-mesh.org/projects/batman-adv/wiki) Most of the original developers of batmand jumped ship to batman-adv, a completely new take on the algorithm. Unlike all other implementations on this list besides open80211s, batman-adv runs on layer 2 and routes ethernet frames rather than UDP packets. This has a lot of advantages but also some significant disadvantages. Included as part of the Linux kernel, it's basically written into some of the Linux WiFi stack. Predominantly maintained by Freifunk (see below).

* [bmx6/7:](http://bmx6.net/projects/bmx6) Originally a fork of batmand, bmx6 (now moving up to version 7) is an extremely complex and sophisticated self-configuring routing protocol with high performance and low overhead. Predominantly maintained by Guifi (see below).

* [open80211s:](http://www.o11s.org/) The linux wireless stack's implementation of the IEEE 802.11s standard for WiFi mesh. 802.11s as designed had serious shortcomings compared to other protocols (was largely meant for tiny in-home networks of less than a dozen devices). The open implementation has a number of improvements, but inconsistent hardware support.

## Firmwares ##

Most work takes place on OpenWRT or now its fork LEDE, a Linux distribution for wireless routers, which consequently also serves as a bleeding-edge WiFi testbed. There's significant overlap between the OpenWRT/LEDE head developers, the Freifunk community network, the C-base hacker space, and the Chaos Computer Club, all centered in Berlin. There are a number of distributions based on OpenWRT/LEDE used by various networks:

* [Freifunk:](https://freifunk.net//en/) The Freifunk network has used a number of firmwares over the years, and most of their stuff is included in the default OpenWRT package treOther networkse. The latest firmware is called gluon and uses batman-adv.

* [qMP:](http://qmp.cat/Home) The Quick Mesh Project, a subproject of Guifi.net that has an auto-configuring firmware using bmx7.

* [LibreMesh:](http://libremesh.org/) A project of Altermundi, LibreMesh is more of a meta-build system. It can create qMP and gluon compatible firmwares, and is used for creating hybrid networks using batman-adv and bmx7 together in order to get around the disadvantages of each.

* [Nodewatcher:](https://nodewatcher.readthedocs.io/en/development/) Nodewatcher is actually a network-wide dashboard with a built-in build system for the wlan slovenija network. All configuration takes place using the dashboard and a custom firmware is created for each physical device, so it follows a different model than many of the others. Used batman-adv but is transitioning to Babel. Nodewatcher's technically the dashboard, but I don't know if there's a separate name for the firmware.

* [Commotion:](https://commotionwireless.net/) Commotion is a suite of open-source communications tools that use wireless devices to create decentralized mesh networks and share local services, focused on ease of use and security (note: the software is currently in maintenance mode during a major rewrite).

* [Serval Project:](http://www.servalproject.org/) An Australian project centered around providing encrypted mobile communication without infrastructure in the event of a disaster or for use in sparsely populated areas like the Australian Outback. A partner of the Commotion project.


## Hardware ##

* [Librerouter:](https://librerouter.org/) A project operated by Altermundi in partnership with a small open-source friendly hardware vendor called Dragino, Librerouter is an attempt to create a router actually designed for large-scale community wireless networks in response to the increasing regulatory lockdown of WiFi hardware.

* [Meshpoint:](http://www.meshpoint.me/) An open-hardware project to design and build rugged autonomous hardware for building networks and services in refugee camps and disaster areas. Loose connections to the wlan slovenija network.

* [Koruza:](http://koruza.net/) An project run by some of the people from wlan slovenija around creating hardware for self-focusing freespace optics (laser) networking hardware.

* [Open Mesh:](http://www.open-mesh.com/) Commercial hardware for mesh networking.

* [Cisco Meraki:](https://meraki.cisco.com/) Commercial hardware for mesh networking.

## Large Community Wireless Networks ##

* [Guifi.net:](http://guifi.net/en/node/38392) The largest community network, as of writing it has 32,761 nodes throughout much of Catalonia, Spain. A heterogenous network, they basically run their own backbone using BGP and OSPF, and many participating communities connect to it with a variety of technologies, including some of the stuff listed above.

* [Freifunk:](https://freifunk.net//en/) A group of networks, mostly in cities throughout Germany, centered in Berlin. One of the most influential in the larger communities due to its long history and overlap with the various development and hacker communities in Berlin.

* [Funkfeuer:](https://www.funkfeuer.at/) A group of networks in Austria, mostly in Vienna and Graz. The Vienna network is one of the largest single-uplink homogenous WiFi meshes, with around 600 nodes.

* [AWMN:](http://www.awmn.net/content.php?s=a94501c89ad9960a487663c2466311bf) The Athens Wireless Metropolitan Network, AWMN is probably the second largest network with about 3000 nodes. It is an extremely heterogenous network that uses a variety of technologies and is operated in a very decentralized fashion. Originally operated as a large-scale intranet without any internet access.

* [wlan slovenija:](https://wlan-si.net/) A large network in Slovenija, wlan slovenija runs a large network operating on top of the Nodewatcher system. They're also involved in the Meshpoint project around creating rugged router equipment for refugee camps and disaster zones, and the Koruza project around creating open hardware freespace optics (lasers) for networking.

* [Ninux:](http://ninux.org/FrontPage) A long-running community wireless network in various parts of Italy.

## Small Community Wireless Networks ##

* [Altermundi:](https://www.altermundi.net/) Based in Argentina, Altermundi provides tools for communities to build networks. Heads up Libremesh and other associated projects like Altermap.

* [Sudomesh:](https://sudoroom.org/wiki/Mesh) A project by the Sudo Room hackerspace, Sudo Mesh is building the People's Own Network in Oakland, CA.

* [Reseau Libre:](https://wiki.reseaulibre.ca/) The successor of Ile Sans Fil in Montreal, Reseau Libre builds and maintains a community wireless network in downtown Montreal.

* [Metamesh:](http://www.metamesh.org/) A project to build and operate a wireless mesh network and build community wireless toolkits in Pittsburgh, PA.

* [Detroit Community Technology Project:](https://www.alliedmedia.org/dctp) Amongst other programs, operates or assists with multiple community wireless networks in Detroit, MI.

* [Redhook WiFi:](http://redhookwifi.org/) Operates a community wireless network and training program in the Redhook neighborhood of Brooklyn, NY.

* [NYC Mesh:](https://nycmesh.net/) A relatively new project to build a wireless mesh network in various neighborhoods in NYC.

* [RISE NYC:](https://www.newamerica.org/resilient-communities/flexible-future-ready-networks/rise-nyc/) A project to create disaster-resilient community wireless infrastructure and practices in NYC.

* [WasabiNet:](http://gowasabi.net/) A community-oriented wireless ISP in St. Louis, MO.

## Defunct/Inactive Community Wireless Networks ##

* [MIT Roofnet:](https://en.wikipedia.org/wiki/Roofnet) Historically one of the first community wireless mesh networks, Roofnet is now largely defunct (though occasionally someone picks it up again). Many of the people from Roofnet started up commercial mesh company Meraki, now bought by Cisco (see above).

* [CUWiN/Cuwireless:](https://en.wikipedia.org/wiki/Champaign-Urbana_Community_Wireless_Network) The Champaign-Urbana Wireless Network, another of the first open-source community wireless networks centered in Champaign-Urbana, IL, which is now defunct.
