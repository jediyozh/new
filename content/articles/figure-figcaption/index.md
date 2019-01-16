---
title: "Элементы figure и figcaption"
date: "2012.03.12"
---

# Элементы figure и figcaption

[Ричард Кларк](http://richclarkdesign.com/) 12 марта 2012

В обычных печатных изданиях, таких как книги и журналы, изображения, таблицы или примеры кода обычно сопровождаются подписью. До сих пор у нас не было возможности семантически выделять такой тип содержимого напрямую в HTML, вместо того чтобы прибегать к именам классов СSS. HTML5 надеется исправить эту проблему с помощью новых элементов: `<figure>` и `<figcaption>`. Давайте разберемся!

## Элемент `<figure>`

Предполагается, что элемент `<figure>` будет использоваться в сочетании с элементом `<figcaption>` для того, чтобы выделять диаграммы, иллюстрации, фотографии и примеры кода (помимо прочего). Вот что говорится о `<figure>` в спецификации:

> Элемент `<figure>` представляет собой фрагмент независимого содержимого, совсем необязательно с подписью, который как правило относится к отдельному элементу из основного содержимого документа, и может быть удалён из документа без ущерба его смыслу.
> [Спецификация W3C](http://dev.w3.org/html5/markup/figure.html)

## Элемент `<figcaption>`

Этот элемент стал [поводом](http://adactio.com/journal/1604/) [серьезных](http://remysharp.com/2009/08/12/saving-figure-detail/) [споров](http://html5doctor.com/legend-not-such-a-legend-anymore/). Спецификация изначально предлагала приспособить для этих целей элемент `<legend>`, вместо того, чтобы придумывать новый элемент. Были и другие предложения, включавшие `<label>`, `<caption>`, `<p>` и даже заголовки `<h1>`—`<h6>`. Семантика элемента `<legend>` [изменилась](http://html5doctor.com/legend-not-such-a-legend-anymore/), и поэтому мы начали использовать комбинацию `<dt>` и `<dd>` внутри `<figure>` по предложению [Джереми](http://twitter.com/adactio). Но большинство этих идей были отклонены из-за отсутствия обратной совместимости для CSS-оформления.

Наши постоянные читатели знают, что недавно [был представлен новый элемент](http://html5doctor.com/summary-figcaption-element/) `<figcaption>`. Кто знает, приживется ли он, а пока давайте узнаем, что о нём говорит спецификация:

> Элемент `<figcaption>` представляет собой заголовок или описание для `<figure>`.
>
> [Спецификация W3C](http://dev.w3.org/html5/markup/figcaption.html)

Элемент `<figcaption>` является необязательным и может появляться до _или_ после содержимого внутри `<figure>`. Только один элемент `<figcaption>` может быть помещен в `<figure>`, хотя сам элемент `<figure>` может содержать несколько дочерних элементов (например, `<img>` или `<code>`).

## Использование `<figure>` и `<figcaption>`

Итак, мы узнали, что об этих элементах говорится в спецификации. Как же их использовать? Давайте рассмотрим это на примерах.

### `<figure>` для изображения

Изображение в элементе `<figure>` без подписи:

<figure>
    <img src="images/orang-utan.jpg" alt="Малыш орангутанга свисает с каната.">
</figure>

Вот код для этого:

    <figure>
        <img src="orang-utan.jpg"
             alt="Малыш орангутанга свисает с каната.">
    </figure>

### `<figure>` с изображением и подписью

Изображение внутри элемента `<figure>` с поясняющей подписью:

<figure>
    <img src="images/macaque.jpg" alt="Макака на дереве.">
    <figcaption>Наглая макака из Борнео. Фото <a href="http://www.flickr.com/photos/rclark/102352241/in/set-72057594082373448/">Ричарда Кларка</a></figcaption>
</figure>

И код, который мы использовали:

    <figure>
        <img src="macaque.jpg" alt="Макака на дереве.">
        <figcaption>
            Наглая макака из Борнео.
            Фото <a href="…">Ричарда Кларка</a>
        </figcaption>
    </figure>

### `<figure>` с несколькими изображениями

Размещение нескольких изображений внутри одного элемента `<figure>` с общей подписью:

<figure>
    <img src="images/kookaburra.jpg" alt="Кукабара.">
    <img src="images/pelican.jpg" alt="Пеликан на пляже.">
    <img src="images/lorikeet.jpg" alt="Наглый многоцветный лорикет.">
    <figcaption>
        Слева направо: кукабара, пеликан и многоцветный лорикет.
        Фотографии <a href="http://www.flickr.com/photos/rclark/">Ричарда Кларка</a>
    </figcaption>
</figure>

И сам код:

    <figure>
        <img src="kookaburra.jpg" alt="Кукабара.">
        <img src="pelican.jpg" alt="Пеликан на пляже.">
        <img src="lorikeet.jpg" alt="Наглый многоцветный лорикет.">
        <figcaption>
            Слева направо: кукабара, пеликан и многоцветный лорикет.
            Фотографии <a href="…">Ричарда Кларка</a>
        </figcaption>
    </figure>

### `<figure>` с блоком кода

Элемент `<figure>` может быть также использован для примеров кода:

<figure>
    <blockquote>
        <p><code><small>
            <a rel="license" href="http://creativecommons.org/licenses/by-sa/3.0/">
                Creative Commons Attribution Share-alike license
            </a>
        </small></code></p>
    </blockquote>
    <figcaption>
        Использование элемента <code>&lt;small&gt;</code> вокруг ссылки на лицензию Creative Commons с <code>rel="license"</code>.
    </figcaption>
</figure>

Ниже приведен код для этого:

    <figure>
        <blockquote>
            <p><code><small>
                <a rel="license" href="…">
                    Creative Commons Attribution Share-alike license
                </a>
            </small></code></p>
        </blockquote>
        <figcaption>
            Использование элемента <code>&lt;small&gt;</code>
            вокруг ссылки на лицензию Creative Commons
            с <code>rel="license"</code>.
        </figcaption>
    </figure>

### Различия между `<figure>` и `<aside>`

Мы уже говорили об элементе `<aside>` [в предыдущей статье](http://html5doctor.com/aside-revisited/), но важно отметить разницу между ними. При выборе между `<aside>` или `<figure>`, стоит спросить себя, имеет ли содержимое элемента важное значение для понимания содержимого:

- Если содержимое просто имеет отношение и не является существенным, то используйте `<aside>`.
- Если содержимое является важным, но его положение в потоке общего содержимого не так важно, используется элемент `<figure>`.

Обратите внимание, что если положение содержимого в тексте тесно связано с предыдущим и последующим содержимым, следует использовать более подходящие элементы — например, `<div>`, старый добрый `<img>`, `<blockquote>`, или даже `<canvas>`, в зависимости от типа содержимого.

## Не останавливайтесь на достигнутом!

Не стоит ограничивать использование `<figure>` изображениями и примерами кода. Другим содержимым, подходящим по смыслу для использования в элементе `<figure>` может быть аудио, видео, графики (возможно, с использованием `<canvas>` или `<svg>`), стихи или таблицы со статистикой.

Однако использование элемента `<figure>` не всегда целесообразно. Например, графический баннер не стоит размечать в `<figure>`. Используйте для этого просто `<img>`.

## Вывод

Как мы продемонстрировали в этой статье, элемент `<figure>` открывает много возможностей. Только не забудьте убедиться, что он подходходит для конкретного случая. Хотя вряд ли вы бездумно относитесь к разметке, так ведь?

Перевод оригинальной статьи «[The figure & figcaption elements](http://html5doctor.com/the-figure-figcaption-elements/)» [Ричарда Кларка](http://richclarkdesign.com/) (Richard Clark), опубликованной на сайте [HTML5Doctor.com](http://html5doctor.com/).

Перевод выполнила Екатерина Мордвина.