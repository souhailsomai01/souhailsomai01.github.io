---
layout: post
title: Accelerated Mobile Pages
categories: front-end
description: >
tags: []
published: false
social_image: amp/amp_logo.gif
social_width: 564
social_height: 220
social_caption: Google Accelerated Mobile Pages Project
---

Последнюю неделю я переделывал блог с использованием Google Accelerated Mobile Pages Project. Потом еще неделю исправлял ошибки. Сегодня поговорим что такое AMP, в чем его преимущества, за счет чего они достигаются и покажу как это сделать.

<!-- more -->

{% include media-post-image.html %}

## Что такое AMP

AMP это надстройка на HTML, которая вводит свои элементы, ограничевает стандартные возможности и оптимизирует доставку содержимого. На практике AMP состоит из трех частей:

* **AMP HTML** — базовая разметка с надстройками и ограничениями
* **AMP JS** — библиотека компонентов
* **AMP Cache** — amp версия сайта кешируется гуглом и раздается с их серверов обеспечивая максимальную скорость

В совокупности эти три части дают максимальный прирост к скорости.

## Как AMP ускоряет загрузку страниц

Благодаря следующим оптимизациям AMP страницы загружаются быстрее обычных:

1. Асинхронные скрипты
1. Определение размеров всех ресурсов (изображений, видео, iframe)
1. Предотвращение блокировки визуализации механизмами расширений
1. Устранение всех сторонних сценариев JavaScript из основного потока операций
1. Все CSS должны быть встроенными и ограниченными по размеру
1. Переключение шрифта должно быть эффективным
1. Сокращение пересчетов стилей
1. Запуск анимации только с аппаратным ускорением
1. Приоритетная загрузка ресурсов
1. Мгновенная загрузка страниц

Я не буду подробно расписывать каждый аспект, вы можете сами прочитать об этом на [странице проекта](https://www.ampproject.org/ru/learn/how-amp-works/).

## Теория использования АМП

Поддержку АМП на сайте можно реализовать двумя путями:

1. Дополнительно создать урезанную версию сайта с использованием АМП
1. Урезать основную версию и использовать АМП прямо на ней

Оба метода имеют свои плюсы и минусы. Чаще всего у вас не будет выбора, поскольку в АМП страницах не работает ваш JavaScript. Если функционал вашего ресурса вплотную завязан на него, то вы будите вынуждены урезать его и делать отдельную АМП версию.

Если же у вас обычные статьи, то скорее всего можно привести её к АМП формату и поддерживать только одну версию сайта, а не две как в предыдущем случае. Этот способ я использую у себя.

Хорошей практикой будет выявить ваши основные страницы, которые чаще всего читают люди и добавить к ним АМП версию. Это никак не затронет основной сайт, а людям будет удобнее читать вас.

## Ограничения

Выше я предупредил вас о невозможности использовать JavaScript на АМП версии сайта, но это далеко не все ограничения.

1. У всех медиа файлов должны быть указаны размеры
1. CSS должно быть мало и он должен быть заинлайнен в `head`
1. У всех АМП страниц формата `BlogPost` должна быть картинка
1. Поддерживаются только последние 2 версии популярных браузеров
1. Часто придется перелопатить много кода, чтобы все заработало
1. `iframe` с вашего домена недоступен, если нужно что-то встроить через `iframe` —  вам нужен другой домен или субдомен
1. Аналитика из Яндекс.Метрики не работает

Даже если вас не смущают эти ограничения, я не рекомендую бросаться с головой и переписывать весь проект. Попробуйте для начала добавить АМП версию к вашей новой статье. Проверьте стоит ли это затраченных усилий.

## <span>«</span>Привет мир!»
Цель: Убедить использовать АМП
Как убедить: Рассказать о преимуществах, как достигается, кто поддерживает
Альтернативы?
Примеры

теория — практика

Введение (что это) – освежить знания, интерес/польза (в этой статье вы научитесь)
Как работает
Как использовать
Кто поддерживает
Итог (чеклист, таблица, рецепты)
Дополнительные материалы