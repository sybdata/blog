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

## с 26.10.2020 перестал учавствовать в Форуме(forumtv.site)! 
## Все вопросы и запросы для получения расшифрованого плейлиста направлять на [streamfaster@id500.de](streamfaster@id500.de)

### Вначале выберем язык на котором понятней и удобней и открываем стартовую страницу: https://www.oracle.com/ru/index.html
### идём в -> "Oracle Cloud Infrastructure" -> "Опробовать бесплатный уровень" 
![2020-09-23 (1)](https://user-images.githubusercontent.com/24189833/94052304-09a8a800-fdd9-11ea-9e9e-ec666a0c8445.png)

### далее ознакомимся с условиями и с перечнем бесплатного пакета "Always Free"
![2020-09-23 (2)](https://user-images.githubusercontent.com/24189833/94052908-e5999680-fdd9-11ea-8693-7f1212ad5061.png)

![2020-09-23 (3)](https://user-images.githubusercontent.com/24189833/94053329-7ec8ad00-fdda-11ea-8fc3-3abd958a177b.png)

### жмём на "начните с бесплатной версии" и поехали...
![2020-09-23 (5)](https://user-images.githubusercontent.com/24189833/94059611-f569a880-fde2-11ea-8266-17e990548b6c.png)
![2020-09-23 (6)](https://user-images.githubusercontent.com/24189833/94059953-7628a480-fde3-11ea-966a-0c8b9f90b9e5.png)

### дальше нужно пройти 2 верификации, по смс и по кредитке (кнопка "start my free.." уже видна и держим на неё курс)
![2020-09-23 (7)](https://user-images.githubusercontent.com/24189833/94060498-58a80a80-fde4-11ea-8b58-8f0d6f9f136e.png)
![2020-09-23 (8)](https://user-images.githubusercontent.com/24189833/94060862-e683f580-fde4-11ea-97aa-4be7960d2126.png)
![2020-09-23 (9)](https://user-images.githubusercontent.com/24189833/94061125-424e7e80-fde5-11ea-85ee-c352b6d57789.png)
![2020-09-23 (10)](https://user-images.githubusercontent.com/24189833/94061457-b426c800-fde5-11ea-9059-072543573d73.png)
### если всё в порядке то получаем "зелёный свет"

![2020-09-23 (11)](https://user-images.githubusercontent.com/24189833/94061629-eb957480-fde5-11ea-9620-8272fbfa3441.png)

### и теперь кнопка "start my free.." наконец то доступна

![2020-09-23 (13)](https://user-images.githubusercontent.com/24189833/94062458-fef50f80-fde6-11ea-81f6-94ed9fa52552.png)
### жмакаем и мы на месте
![2020-09-23 (14)](https://user-images.githubusercontent.com/24189833/94062725-53988a80-fde7-11ea-84fa-d0d5f0453978.png)
### обзываем свой будущий сервер
![2020-09-23 (15)](https://user-images.githubusercontent.com/24189833/94062971-b38f3100-fde7-11ea-987d-900a0da00600.png)
### выбираем ОСь
![2020-09-23 (16)](https://user-images.githubusercontent.com/24189833/94063137-f3eeaf00-fde7-11ea-8e0c-f0ad9660d42b.png)
### бесплатные машины доступны только на AD3!
![2020-09-23 (17)](https://user-images.githubusercontent.com/24189833/94063430-62cc0800-fde8-11ea-8e09-fa5904072e1a.png)
### теперь выбираем саму машину и главное не промахнутся
![2020-09-23 (18)](https://user-images.githubusercontent.com/24189833/94063819-fa315b00-fde8-11ea-984b-ab714eb7bbb7.png)
![2020-09-23 (19)](https://user-images.githubusercontent.com/24189833/94064091-6d3ad180-fde9-11ea-82b6-23136b6ac982.png)
![2020-09-23 (20)](https://user-images.githubusercontent.com/24189833/94064229-a5daab00-fde9-11ea-90b9-86b2d2e28f50.png)
### генерируем с puttygen.exe пару ключей и копируем паблик на сервер а приватный сохраняем на компе, потом понадобится...
![2020-09-23 (22)](https://user-images.githubusercontent.com/24189833/94065027-d707ab00-fdea-11ea-831e-7a3e06e6f0ac.png)
![2020-09-23 (23)](https://user-images.githubusercontent.com/24189833/94065248-2d74e980-fdeb-11ea-92c8-adb21d57c748.png)
### в дополнительных настройках выключаем мониторинг, остальное по умолчанию, и жмём "создать"
![2020-09-23 (24)](https://user-images.githubusercontent.com/24189833/94065588-a83e0480-fdeb-11ea-9192-47ab1052de10.png)

### настроим putty и попробуем зайти на сервер через ssh
![2020-09-23 (26)](https://user-images.githubusercontent.com/24189833/94066505-da039b00-fdec-11ea-8843-670fe5c9a64a.png)
![2020-09-23 (27)](https://user-images.githubusercontent.com/24189833/94066758-35358d80-fded-11ea-8cb3-bbebb0f67b2d.png)
![2020-09-23 (28)](https://user-images.githubusercontent.com/24189833/94067238-de7c8380-fded-11ea-969f-7bff39694061.png)
### здесь соглашаемся
![2020-09-23 (29)](https://user-images.githubusercontent.com/24189833/94067482-34e9c200-fdee-11ea-9790-67ca0f4dbba0.png)
### всё мы вошли
![2020-09-23 (30)](https://user-images.githubusercontent.com/24189833/94067786-a88bcf00-fdee-11ea-8754-2b758fec8216.png)
### получаем рут и работаем
![2020-09-23 (31)](https://user-images.githubusercontent.com/24189833/94068049-fb658680-fdee-11ea-9c0b-30fb79c058ab.png)
![2020-09-23 (32)](https://user-images.githubusercontent.com/24189833/94068245-38317d80-fdef-11ea-8f68-8cd065192236.png)
![2020-09-23 (33)](https://user-images.githubusercontent.com/24189833/94068481-88104480-fdef-11ea-97bb-68cc0f640019.png)
### на мыло придёт два письма с краткими даными учётки с "кнопками" по которым и можно заходить на свою учётку

![2020-09-23 (34)](https://user-images.githubusercontent.com/24189833/94069184-71b6b880-fdf0-11ea-8a19-ccd21d2d6798.png)
![2020-09-23 (35)](https://user-images.githubusercontent.com/24189833/94069238-83985b80-fdf0-11ea-8006-26aa4b3f8b3e.png)


# enjoy
# Дополнительно(Бонус)
## Использование сети маршрутизации в режиме кластера
![ingress-routing-mesh](https://user-images.githubusercontent.com/24189833/95024190-d17b5200-0681-11eb-9277-a6d5be892b70.png)
### Открыть протоколы и порты между хостами
Следующие порты должны быть доступны:

 * TCP port 2377  для управления кластером
 * TCP and UDP port 7946 для связи между узлами
 * UDP port 4789  для оверлейного сетевого трафика
 
 ### Создание кластера
 #### Откройте терминал и подключитесь по ssh к машине, на которой вы хотите запустить свой управляющий узел и выполните следующюю команду:
 ```ruby
 $ docker swarm init --advertise-addr 192.168.99.100
Swarm initialized: current node (dxn1zf6l61qsb1josjja83ngz) is now a manager.

To add a worker to this swarm, run the following command:

    docker swarm join \
    --token SWMTKN-1-49nj1cmql0jkz5s954yi3oex3nedyz0fb0xx14ie39trti4wxv-8vxv8rssmk743ojnwacrr2e7c \
    192.168.99.100:2377

To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.
 ```
 
#### Откройте терминал и подключитесь по ssh к машине, на которой вы хотите запустить второй рабочий узел.
#### Запустите команду, созданную выходными данными docker swarm init из первого шага, чтобы создать второй рабочий узел, присоединенный к существующему swarm:
```ruby
$ docker swarm join \
  --token SWMTKN-1-49nj1cmql0jkz5s954yi3oex3nedyz0fb0xx14ie39trti4wxv-8vxv8rssmk743ojnwacrr2e7c \
  192.168.99.100:2377

This node joined a swarm as a worker.
```
### Разверните сервис в кластере
#### Откройте терминал и подключитесь по ssh к машине, на которой вы запустили управляющий узел и выполните следующую команду:
```ruby
docker service create --replicas 4 --name zmp_cluster --publish published=1010,target=1010 sybdata/ace86a37:zproxy

```
![2020-10-04 (1)](https://user-images.githubusercontent.com/24189833/95024782-a3980c80-0685-11eb-9d08-248f573d17fe.png)

![2020-10-04 (2)](https://user-images.githubusercontent.com/24189833/95025247-9f212300-0688-11eb-8cb5-bd7ec1bec82a.png)


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
