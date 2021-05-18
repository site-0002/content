---
title: 'Установка статического IP адреса'
description: ''
images:
  - 'https://images.unsplash.com/photo-1544197150-b99a580bb7a8'
categories:
  - 'Terminal'
tags:
  - 'ip'
authors:
  - 'KitsuneSolar'
licenses:
  - 'cc-by-sa-4.0'

date: '2021-05-15T20:08:30+03:00'
hash: 'ee559a6c5cde1166bd2d3ceb55878eb8b7d7e436'
uuid: 'ee559a6c-5cde-5166-9d2d-3ceb55878eb8'
slug: 'ee559a6c-5cde-5166-9d2d-3ceb55878eb8'

comments: 1
feedback: 1
draft: 1
---

```text
ip a
```

```text
ip address add 192.168.1.25/255.255.255.0 dev eth0
```

```text
ip address flush dev eth0
```

```text
ip link set dev eth0 up
```

```text
ip link set dev eth0 down
```
