---
title: "Ceph - turns out to be a giant PITA(Pain in the ass) "
date: 2019-07-05T15:34:30-04:00
categories:
  - Storage
tags:
  - Ceph Object Storage
  - Ceph Filesystem
  - Ceph Storage Cluster
  - Ceph Block Device
---
{% include figure image_path="https://sybdata.de/sphinx/_images/ditaa-409784e9076840f895f8cbd328a523961cda0d87.png" alt="this is a placeholder image" caption="" %}
```ruby
[root@ds1 /]# ceph -s
  cluster:
    id:     4bf42ffc-eccb-48c2-aa74-7d82aa72196c
    health: HEALTH_WARN
            mons ds1,ds2,ds3 are low on available space

  services:
    mon: 3 daemons, quorum ds1,ds2,ds3
    mgr: ds1(active), standbys: ds2, ds3
    mds: cephfs-1/1/1 up  {0=ds1=up:active}, 2 up:standby
    osd: 3 osds: 3 up, 3 in

  data:
    pools:   2 pools, 251 pgs
    objects: 21 objects, 2.19KiB
    usage:   3.01GiB used, 147GiB / 150GiB avail
    pgs:     251 active+clean
```
{% include figure image_path="https://sybdata.de/sphinx/_images/mds-state-diagram.svg" alt="this is a placeholder image" caption="" %}
