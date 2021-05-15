---
title: 'Разнообразие команд ls*'
description: ''
images:
  - 'https://images.unsplash.com/photo-1507925921958-8a62f3d1a50d'
categories:
  - 'Terminal'
  - 'InDev'
tags:
  - 'linux'
  - 'terminal'
  - 'ls'
authors:
  - 'KitsuneSolar'
licenses:
  - 'cc-by-sa-4.0'

date: '2021-05-09T16:44:05+03:00'
hash: '5ba03b8a05058d800fadf7a4d66f07b025f46bb7'
uuid: '5ba03b8a-0505-5d80-bfad-f7a4d66f07b0'
slug: '5ba03b8a-0505-5d80-bfad-f7a4d66f07b0'

comments: 1
feedback: 1
draft: 0
---

Команда `ls` и её разновидности позволяют вывести список директорий, файлов, устройств и различной другой информации. Я расскажу только о некоторых командах `ls*`, которые присутствуют в большинстве дистрибутивов Linux.

<!--more-->

Знаю, что есть `lsscsi`, `lsusb` и т.п., которые появляются в системе с установкой дополнительных пакетов, но я подобные команды рассматривать не стал. Хотя, по возможности, статью буду дополнять.

## ls

Команда позволяет вывести список директорий и файлов в текущем каталоге.

#### Некоторые опции

- `-l` - использовать длинный формат отображения.
- `-S` - сортировать по размеру файла.
- `-t` - сортировать по времени модификации.
- `-a` - показать ВСЕ файлы, в том числе скрытые.
- `-R` - рекурсивное отображение директорий и файлов в них.
- `-h` - отображение размеров файлов в человеко-читаемом формате.
- `--hide='*.txt' -l` - игнорировать файлы с форматом `.txt`.

## lscpu

Отображение доступной информации об установленном процессоре.

#### Некоторые опции

- `-a` - показать ВСЕ CPU, как включённые, так и отключённые.

#### Пример использования

```txt
user@localhost ~ % lscpu

Architecture:                    x86_64
CPU op-mode(s):                  32-bit, 64-bit
Byte Order:                      Little Endian
Address sizes:                   39 bits physical, 48 bits virtual
CPU(s):                          12
On-line CPU(s) list:             0-11
Thread(s) per core:              2
Core(s) per socket:              6
Socket(s):                       1
NUMA node(s):                    1
Vendor ID:                       GenuineIntel
CPU family:                      6
Model:                           165
Model name:                      Intel(R) Core(TM) i5-10400 CPU @ 2.90GHz
Stepping:                        5
CPU MHz:                         2900.000
CPU max MHz:                     4300.0000
CPU min MHz:                     800.0000
BogoMIPS:                        5799.77
L1d cache:                       192 KiB
L1i cache:                       192 KiB
L2 cache:                        1.5 MiB
L3 cache:                        12 MiB
```

## lspci

Отображение информации по шине PCI и подключённых к ней устройствах.

#### Пример использования

```txt
user@localhost ~ % lspci

00:00.0 Host bridge: Intel Corporation Comet Lake-S 6c Host Bridge/DRAM Controller (rev 05)
00:01.0 PCI bridge: Intel Corporation 6th-10th Gen Core Processor PCIe Controller (x16) (rev 05)
00:14.0 USB controller: Intel Corporation Comet Lake USB 3.1 xHCI Host Controller
00:14.2 RAM memory: Intel Corporation Comet Lake PCH Shared SRAM
00:14.3 Network controller: Intel Corporation Comet Lake PCH CNVi WiFi
00:15.0 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH Serial IO I2C Controller #0
00:15.1 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH Serial IO I2C Controller #1
00:16.0 Communication controller: Intel Corporation Comet Lake HECI Controller
00:17.0 SATA controller: Intel Corporation Comet Lake SATA AHCI Controller
00:1d.0 PCI bridge: Intel Corporation Comet Lake PCI Express Root Port #9 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Device 0684
00:1f.3 Audio device: Intel Corporation Comet Lake PCH cAVS
00:1f.4 SMBus: Intel Corporation Comet Lake PCH SMBus Controller
00:1f.5 Serial bus controller [0c80]: Intel Corporation Comet Lake PCH SPI Controller
00:1f.6 Ethernet controller: Intel Corporation Ethernet Connection (11) I219-V
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Baffin [Radeon RX 550 640SP / RX 560/560X] (rev cf)
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Baffin HDMI/DP Audio [Radeon RX 550 640SP / RX 560/560X]
```

## lsblk

Отображение информации по блочным устройствам.

#### Пример использования

```
user@localhost ~ % lsblk

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 232.9G  0 disk
├─sda1   8:1    0   200M  0 part /boot/efi
├─sda2   8:2    0     4G  0 part /boot
├─sda3   8:3    0    64G  0 part /
├─sda4   8:4    0    32G  0 part [SWAP]
├─sda5   8:5    0    16G  0 part /tmp
└─sda6   8:6    0 116.7G  0 part /home
sdb      8:16   0 465.8G  0 disk
└─sdb1   8:17   0 465.8G  0 part /home/storage.01
sdc      8:32   1 119.5G  0 disk
└─sdc1   8:33   1 119.5G  0 part /run/media/user-0001/USB01
sdd      8:48   1  59.8G  0 disk
├─sdd1   8:49   1  59.7G  0 part /run/media/user-0001/Ventoy
└─sdd2   8:50   1    32M  0 part /run/media/user-0001/VTOYEFI
zram0  252:0    0     4G  0 disk [SWAP]
```

## lsmod

Отображение модулей ядра, загруженных в системе.

#### Пример использования

```
user@localhost ~ % lsmod

Module                  Size  Used by
exfat                  81920  1
f2fs                  700416  1
uas                    32768  0
usb_storage            81920  4 uas
snd_seq_dummy          16384  0
rfcomm                 90112  0
snd_hrtimer            16384  1
xt_CHECKSUM            16384  1
xt_MASQUERADE          20480  3
xt_conntrack           16384  1
ipt_REJECT             16384  2
nft_compat             20480  16
nf_nat_tftp            16384  0
nft_objref             16384  1
nf_conntrack_tftp      20480  3 nf_nat_tftp
nft_counter            16384  33
tun                    57344  1
bridge                294912  0
stp                    16384  1 bridge
llc                    16384  2 bridge,stp
```
