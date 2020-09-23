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

## Запустите собственный сервер в Oracle Cloud Infrastructure

### Вначале выберим язык на котором понятней и удобней и открываем стартовую страницу: https://www.oracle.com/ru/index.html
идём в -> "Oracle Cloud Infrastructure" -> "Опробовать бесплатный уровень" 
![2020-09-23 (1)](https://user-images.githubusercontent.com/24189833/94052304-09a8a800-fdd9-11ea-9e9e-ec666a0c8445.png)

далее ознакомимся с условиями и с перечнем бесрлатного пакета "Always Free"
![2020-09-23 (2)](https://user-images.githubusercontent.com/24189833/94052908-e5999680-fdd9-11ea-8693-7f1212ad5061.png)

![2020-09-23 (3)](https://user-images.githubusercontent.com/24189833/94053329-7ec8ad00-fdda-11ea-8fc3-3abd958a177b.png)

жмём на "начните с бесплатной версии" и поехали...
![2020-09-23 (5)](https://user-images.githubusercontent.com/24189833/94059611-f569a880-fde2-11ea-8266-17e990548b6c.png)
![2020-09-23 (6)](https://user-images.githubusercontent.com/24189833/94059953-7628a480-fde3-11ea-966a-0c8b9f90b9e5.png)

дальше нужно пройти 2 верификации, по смс и по кредитке (кнопка "start my free.." уже видна и держим на неё курс)
![2020-09-23 (7)](https://user-images.githubusercontent.com/24189833/94060498-58a80a80-fde4-11ea-8b58-8f0d6f9f136e.png)
![2020-09-23 (8)](https://user-images.githubusercontent.com/24189833/94060862-e683f580-fde4-11ea-97aa-4be7960d2126.png)
![2020-09-23 (9)](https://user-images.githubusercontent.com/24189833/94061125-424e7e80-fde5-11ea-85ee-c352b6d57789.png)
![2020-09-23 (10)](https://user-images.githubusercontent.com/24189833/94061457-b426c800-fde5-11ea-9059-072543573d73.png)
если всё в порядке то получаем "зелёный свет"
![2020-09-23 (11)](https://user-images.githubusercontent.com/24189833/94061629-eb957480-fde5-11ea-9620-8272fbfa3441.png)
и теперь кнопка "start my free.." наконец то доступна
![2020-09-23 (13)](https://user-images.githubusercontent.com/24189833/94062458-fef50f80-fde6-11ea-81f6-94ed9fa52552.png)
жмакаем и мы на месте
![2020-09-23 (14)](https://user-images.githubusercontent.com/24189833/94062725-53988a80-fde7-11ea-84fa-d0d5f0453978.png)
обзываем свой будущий сервер
![2020-09-23 (15)](https://user-images.githubusercontent.com/24189833/94062971-b38f3100-fde7-11ea-987d-900a0da00600.png)
выбираем ОСь
![2020-09-23 (16)](https://user-images.githubusercontent.com/24189833/94063137-f3eeaf00-fde7-11ea-8e0c-f0ad9660d42b.png)
бесплатные машины доступны только на AD3!
![2020-09-23 (17)](https://user-images.githubusercontent.com/24189833/94063430-62cc0800-fde8-11ea-8e09-fa5904072e1a.png)
теперь выбираем саму машину и главное не промахнутся
![2020-09-23 (18)](https://user-images.githubusercontent.com/24189833/94063819-fa315b00-fde8-11ea-984b-ab714eb7bbb7.png)





## Run your own ZMP Server on Oracle Cloud Infrastructure

If you choose to, register on Oracle Cloud (requires credit card for verification) and create a free VM:

 * Create a VM instance
 * Give it a name
 * OS/image: Ubuntu 16.04 Minimal or Ubuntu 18.04 Minimal or Ubuntu 20.04 Minimal or CentOS 7
 * Show Shape, Network and Storage Options -> Assign a public IP address
 * [Add SSH key (generate one using ssh-keygen if you don't have one)](https://tech.id500.de/wp/?page_id=201)
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
