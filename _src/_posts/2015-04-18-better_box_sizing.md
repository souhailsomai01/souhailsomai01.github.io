---
layout: post
title: Международный день box-sizing и лучшие практики
categories: front-end
redirect_from:
  - /blog/better_box_sizing/
tags: [лучшие практики, праздники разработчиков, css]
description: >
  Лучшие практики использования CSS свойства box-sizing и праздник посвященный этому свойству.
---


Недавно я использовал в проекте css свойство `box-sizing: border-box`. В процессе этого я узнал про «Международный день box-sizing» (International box-sizing Awareness Day). И хочу рассказать вам что это за праздник, лучшие практики и поддержку свойства box-sizing.

## Международный день box-sizing

Этот мини праздник отмечается 1 февраля каждого года. Первого февраля 2012 года Пол Айриш (Paul Irish) опубликовал свою статью <a href="http://www.paulirish.com/2012/box-sizing-border-box-ftw/">* { Box-sizing: Border-box } FTW</a>. Спустя два года Крис Койер (Chris Coyier) объявил на сайте <a href="https://css-tricks.com/international-box-sizing-awareness-day/">css-tricks.com</a>, что первое февраля будет считаться «Международным днем box-sizing», в честь даты написания статьи Полом.

## Лучшая практика

Раньше для применения модели border-box для всех элементов я часто видел следующий код:

~~~css
*, *:before, *:after {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
~~~


Но он уже устарел и не совсем отвечает современным требованиям. Во первых нам уже не нужны вендорные префиксы для этого свойства (<a href="http://caniuse.com/#feat=css3-boxsizing">пруф</a>). А во вторых, если мы где-то меняем `box-sizing` на `content-box`, то мы ожидаем, что у всех его родителей `box-sizing` будет тоже `content-box`, но с предыдущем кодом так не получается.


Поэтому в 2014 году Крис Койер (Chris Coyier) улучшил этот код, и теперь это считается лучшей практикой для `box-sizing`.

~~~css
html {
    box-sizing: border-box;
}
*, *:before, *:after {
    box-sizing: inherit;
}
~~~


Теперь все элементы ведут себя так, как мы и ожидаем. Все элементы кроме `html` наследуют `box-sizing` от родителя.

## Поддержка браузерами

Я рекомендую использование этого свойства для всех проектов IE8 и выше. Firefox до 28 все еще требует префикс `-moz-`, iOS до 4 версии, Android до версии 2.3 требуют `-webkit-`, но все остальные браузеры используют без префиксов.


## Производительность

Вы можете сказать, что использование универсального селектора `*` очень плохо влияет на производительности. На самом деле `*` настолько же быстрый как `h1`. Он может быть медленный если вы используете что-то на подобии `.foo > *`, поэтому не делайте так.

Приведу пример, опубликованный Полом, в котором он сравнивает производительность сайта New York Times со стандартной моделью W3C и с моделью `border-box`:

<figure itemscope itemtype="http://schema.org/ImageObject">
	<img itemprop="contentUrl" width="607" height="291" src="/img/box_sizing/w3c_vs_borderbox.png" alt="Производительность сайта New York Times со стандартной моделью W3C и с моделью border-box">
	<figcaption itemprop="description">Производительность сайта New York Times со стандартной моделью W3C и с моделью border-box</figcaption>
</figure>


Как вы видите, разница составила не больше 5%. <br>Всем rock, peace and box-sizing !)