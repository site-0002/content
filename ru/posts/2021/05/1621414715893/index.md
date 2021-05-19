---
title: 'Настройка времени в Linux'
description: ''
images:
  - 'https://images.unsplash.com/photo-1501139083538-0139583c060f'
categories:
  - 'Terminal'
tags:
  - 'time'
  - 'timezone'
  - 'hwclock'
authors:
  - 'KitsuneSolar'
licenses:
  - 'cc-by-sa-4.0'

date: '2021-05-15T19:22:34+03:00'
hash: '8bdb6bfec516beed99e405003575d2109a5bd949'
uuid: '8bdb6bfe-c516-5eed-a9e4-05003575d210'
slug: '8bdb6bfe-c516-5eed-a9e4-05003575d210'

comments: 1
feedback: 1
draft: 1
---

## Системные часы

```text
timedatectl status
```

```
               Local time: Sat 2021-05-15 19:44:40 MSK
           Universal time: Sat 2021-05-15 16:44:40 UTC
                 RTC time: Sat 2021-05-15 16:44:40
                Time zone: Europe/Moscow (MSK, +0300)
System clock synchronized: yes
              NTP service: active
          RTC in local TZ: no
```

```text
timedatectl set-ntp true
```

```text
systemctl status systemd-timesyncd
```

```text
systemctl enable systemd-timesyncd --now
```

```text
timedatectl list-timezones
```

```text
timedatectl set-timezone Europe/Moscow
```

```text
timedatectl set-time "yyyy-MM-dd hh:mm:ss"
```

```text
timedatectl set-time "2014-05-26 11:13:54"
```

## Аппаратные часы

```text
hwclock --show
```

```text
hwclock --systohc
```
