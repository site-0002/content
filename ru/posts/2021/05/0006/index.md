---
title: 'Обновление Fedora Linux до последней версии'
description: ''
images:
  - 'https://images.unsplash.com/photo-1585406666850-82f7532fdae3'
categories:
  - 'Terminal'
tags:
  - 'fedora'
  - 'dnf'
  - 'upgrade'
authors:
  - 'KitsuneSolar'
licenses:
  - 'cc-by-sa-4.0'

date: '2021-05-15T23:29:16+03:00'
hash: '0acd3f9d07b732b85facb5cb1cc579e08703392f'
uuid: '0acd3f9d-07b7-52b8-9fac-b5cb1cc579e0'
slug: '0acd3f9d-07b7-52b8-9fac-b5cb1cc579e0'

comments: 1
feedback: 1
draft: 1
---

```text
dnf install dnf-plugin-system-upgrade
```

```text
dnf system-upgrade download --releasever=34
```

```text
dnf system-upgrade reboot
```
