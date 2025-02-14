---
layout: post
title: "Assigning whole IP subnets to a Linux system with AnyIP"
permalink: assigning-whole-ip-subnets-to-network-interfaces-with-anyip
modified_date: 2024-05-23
tags: Linux, Networking
---

## What is AnyIP?
[AnyIP](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=ab79ad14a2d51e95f0ac3cef7cd116a57089ba82){:target="_blank"} is a feature in the Linux kernel networking stack that enables assigning a complete IPv4/IPv6 subnet to a system. Despite sharing similarities to that of the loopback IP block `127.0.0.0/8`, these addresses can't be routed, as specified in [RFC 5735](https://datatracker.ietf.org/doc/html/rfc5735#section-3){:target="_blank"}. Whereas with AnyIP, we can first obtain an IP address within a subnet, then attach an IPv4/IPv6 subnet to the loopback interface and still reach it from other subnets (given there's a route).

<br>
## Configuration and use cases
Assigning an IPv4 subnet to a system can be done with this command: `ip route add local <IPv4 or IPv6 subnet>/<cidr> dev lo`. Connections made to any IP within this subnet now point to this machine as a result.

Concerning the usage of AnyIP, one might make use of this in say, reverse proxies with DDoS protection (like in the case of [Cloudflare's Spectrum](https://blog.cloudflare.com/how-we-built-spectrum/){:target="_blank"}, or simulating a network with different services without using VMs/containers, and so on. In the latter's case, we could have an address within a specified range listen as a web server, another running a DHCP server, and so on. All whilst making it look like they originate from different systems.
