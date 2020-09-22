---
title: "Свой сервер - Решения"
date: 2020-09-22T18:50:30-04:00
categories:
  - Netzwerk
tags:
  - server
  - cloud
  - vps
  - oracle
---

![2020-09-22 (6)](https://user-images.githubusercontent.com/24189833/93932452-84fa5300-fd20-11ea-8465-cb84ce99817f.png)

## Run your own ZMP Server on Oracle Cloud Infrastructure

If you choose to, register on Oracle Cloud (requires credit card for verification) and create a free VM:

 * Create a VM instance
 * Give it a name
 * OS/image: Canonical Ubuntu 18.04 Minimal
 * Show Shape, Network and Storage Options -> Assign a public IP address
 * Add SSH key (generate one using ssh-keygen if you don't have one)
 * Show advanced options. I removed monitoring, since I'll remove the monitoring agent later.

View resources and make sure the instance and boot volume are "Always Free" if you don't intent to pay for them.

Make sure you can ssh to the server (using the ssh key you generated/picked) using the user 'ubuntu' and can use sudo.
### Open firewall
#### Oracle Cloud Security lists
View resources -> Instances -> Select instance -> Virtual Cloud Network -> Public Subnet -> Security Lists -> Default -> Ingress

Open incoming for CIDR 0.0.0.0/0:

 * 22/tcp for SSH (should be open already)
 * xxxx/tcp for ZMP
 * xxxx/tcp for HLS-proxy or Xteve

#### Ubuntu iptables

The Oracle Cloud Ubuntu images come with somewhat restrictive iptables rules by default. Docker manages the instance firewall and we have the Oracle Cloud firewall in front, so let's remove the current firewall to avoid trouble:
```ruby
apt purge netfilter-persistent iptables-persistent
```
### Remove useless stuff (optional)

Oracle cloud includes a somewhat heavy monitoring daemon. We have better use for that memory since current versions of Synapse, the Matrix homeserver, can be memory hungry.
```ruby
snap remove oracle-cloud-agent
apt purge snapd open-iscsi lxd lxcfs
```
### Tune server (optional)

I suggest enabling swap, since there's only 1 GB of RAM.
```ruby
dd if=/dev/zero of=/swap bs=1M count=1k
chmod 0600 /swap
mkswap /swap
swapon /swap
echo '/swap none swap sw 0 0' >> /etc/fstab
```
