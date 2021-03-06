---
layout: Post
lang: ru
title: 'Откуда подключать jQuery'
date: Dec 9, 2009
disqus_identifier: 177 http://nano.sapegin.ru/?p=177
tags:
  - javascript
---

Размышляю о том, откуда лучше подключать JavaScript-библиотеки (главным образом jQuery): со своего хостинга, с [CDN Гугла](https://developers.google.com/speed/libraries/?csw=1) или с Яндекса.

Денис Филонов [пишет](http://dvf.su/2009/12/09/pochemu-gruzit-tolko-so-svoego-servera/), что лучше подключать со своего хостинга, но я с ним немного не согласен.

## За

1. Вероятность наличия файла в кэшэ браузера пользователя. Эти методы сейчас довольно популярны (как и сам jQuery), поэтому если пользователь уже побывал недавно на сайте, подключающем библиотеку из того же места, то она просто возьмётся из кэша браузера.
2. Распараллеливание загрузки. (Для тех браузеров, которые сами не умеют.)
3. Высокая скорость загрузки, правильно настроенное кэширование и сжатие. Если использовать для русскоязычных проектов Яндекс, а для англоязычных Гугл, то загрузаться должно не медленнее, чем со своего хостинга, а то и быстрее. (Похоже, кэширования у Гугла настроено более правильно — они используют Expires на год вперёд, а Яндекс зачем-то ставит Etag.)
4. Автоматическое обновление. Если указать версию 1.3, а не 1.3.2, то будет загружаться последняя версия ветки 1.3. (К сожалению, это относится только к Гуглу).

## Против

1. Лишний запрос на сервер. При размещении у себя можно положить все скрипты в один JS-файл.
2. Сервер с библиотекой может быть недоступен. Хотя для CDN Гугла и Яндекса это мало вероятно.
3. Необходима дополнительная настройка среды, чтобы во время разработки на локальном компьютере бралась локальная же версия.

В общем, я ещё не решил, как буду делать. А пока хочу посмотреть, как делают другие, поэтому написал маленький User JS для Оперы, который показывает в углу текущей страницы, откуда на ней подключен jQuery.
