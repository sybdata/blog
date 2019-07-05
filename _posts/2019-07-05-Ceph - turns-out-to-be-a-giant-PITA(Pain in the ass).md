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

* Monitors: A Ceph Monitor (ceph-mon) maintains maps of the cluster state, including the monitor map, manager map, the OSD map, and the CRUSH map. These maps are critical cluster state required for Ceph daemons to coordinate with each other. Monitors are also responsible for managing authentication between daemons and clients. At least three monitors are normally required for redundancy and high availability.
* Managers: A Ceph Manager daemon (ceph-mgr) is responsible for keeping track of runtime metrics and the current state of the Ceph cluster, including storage utilization, current performance metrics, and system load. The Ceph Manager daemons also host python-based modules to manage and expose Ceph cluster information, including a web-based Ceph Dashboard and REST API. At least two managers are normally required for high availability.
* Ceph OSDs: A Ceph OSD (object storage daemon, ceph-osd) stores data, handles data replication, recovery, rebalancing, and provides some monitoring information to Ceph Monitors and Managers by checking other Ceph OSD Daemons for a heartbeat. At least 3 Ceph OSDs are normally required for redundancy and high availability.
* MDSs: A Ceph Metadata Server (MDS, ceph-mds) stores metadata on behalf of the Ceph Filesystem (i.e., Ceph Block Devices and Ceph Object Storage do not use MDS). Ceph Metadata Servers allow POSIX file system users to execute basic commands (like ls, find, etc.) without placing an enormous burden on the Ceph Storage Cluster.

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
This state diagram shows the possible state transitions for the MDS/rank. The legend is as follows:
Color

   * Green: MDS is active.
   * Orange: MDS is in transient state trying to become active.
   * Red: MDS is indicating a state that causes the rank to be marked failed.
   * Purple: MDS and rank is stopping.
   * Red: MDS is indicating a state that causes the rank to be marked damaged.

Shape

   * Circle: an MDS holds this state.
   * Hexagon: no MDS holds this state (it is applied to the rank).

Lines

   * A double-lined shape indicates the rank is “in”.

{% include figure image_path="https://sybdata.de/sphinx/_images/mds-state-diagram.svg" alt="this is a placeholder image" caption="" %}
