---
title: 'Рекурсивное изменение прав доступа на файлы и директории'
description: ''
images:
  - 'https://images.unsplash.com/photo-1569235186275-626cb53b83ce'
categories:
  - 'Terminal'
tags:
  - 'linux'
  - 'terminal'
  - 'chmod'
  - 'find'
authors:
  - 'KitsuneSolar'
licenses:
  - 'cc-by-sa-4.0'

date: '2021-05-09T20:15:26+03:00'
hash: '4a3b0a310d3d7a9bec077e3b4f80669e95545d6f'
uuid: '4a3b0a31-0d3d-5a9b-8c07-7e3b4f80669e'
slug: '4a3b0a31-0d3d-5a9b-8c07-7e3b4f80669e'

comments: 1
feedback: 1
draft: 0
---

Права доступа к файлам и директориям является неотъемлемой частью любой операционной системы. И в этой статье описаны возможности по рекурсивной настройке этих прав доступа.

<!--more-->

Изменение прав доступа осуществляется при помощи команды `chmod`, рекурсивное при добавлении параметра `-R`:

```
chmod -R MODE DIR
```

- `-R` - рекурсивный обход директорий и файлов.
- `MODE` - набор прав доступа для их установки.
- `DIR` - файл или директория, у которых необходимо установить определённые права доступа.

В итоге, команда должна выглядеть так:

```
user@localhost ~ % chmod -R 755 /var/www/html
```

Но, стоит учитывать, что таким образом директории и файлы примут одинаковые права доступа. Чтобы избежать этого, можно воспользоваться командой `find`, которая отфильтрует директории и файлы друг от друга:

```
user@localhost ~ % find /var/www/html -type d -exec chmod 755 {} \;
user@localhost ~ % find /var/www/html -type f -exec chmod 644 {} \;
```

Команда `find` ищет директории (`-type d`) и файлы (`-type f`) и скармливает их команде `chmod`, а та, в свою очередь, уже расставляет права доступа. При использовании `-exec`, `chmod` выполняется для каждого найденного элемента поочерёдно. Можно оптимизировать и записать с использованием `xargs`:

```
user@localhost ~ % find /var/www/html -type d -print0 | xargs -0 chmod 755
user@localhost ~ % find /var/www/html -type f -print0 | xargs -0 chmod 644
```

При `xargs`, `chmod` выполняется сразу для нескольких записей одновременно, как сообщает **Daniel Miessler**:

{{< quote author="Daniel Miessler" url="https://danielmiessler.com/blog/linux-xargs-vs-exec/" >}}
This is where -exec breaks down and xargs shows its superiority. When you use -exec to do the work you run a separate instance of the called program for each element of input. So if find comes up with 10,000 results, you run exec 10,000 times. With xargs, you build up the input into bundles and run them through the command as few times as possible, which is often just once. When dealing with hundreds or thousands of elements this is a big win for xargs.
{{< /quote >}}

Если необходимо запустить рекурсивное изменение прав доступа начиная с текущей директории, то `/var/www/html` необходимо поменять на точку:

```
user@localhost ~ % find . -type d -print0 | xargs -0 chmod 755
user@localhost ~ % find . -type f -print0 | xargs -0 chmod 644
```
