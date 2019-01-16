---
title: "Элементы i, b, em и strong"
date: "2010.07.13"
---

# Элементы i, b, em и strong

[Оли Стадхольм](http://oli.jp/) 13 июля 2010

В то время как многие элементы из HTML4 вошли в HTML5 без существенных изменений, некоторые исторически презентационные элементы обрели новую семантику.

Давайте посмотрим на `<i>` и `<b>` и сравним их с семантическими преемниками — `<em>` и `<strong>`. Что получается:

- `<i>` — был просто курсивом, а сейчас обозначает _дополнительное выделение_ (например, для иностранных слов, технических терминов) или просто курсивное начертание текста ([W3C:Markup](http://dev.w3.org/html5/markup/i.html), [WHATWG](http://www.whatwg.org/specs/web-apps/current-work/multipage/text-level-semantics.html#the-i-element));
- `<b>` — просто выделял текст полужирным, а сейчас обозначает _стилистическое усиление_ текста (например, для ключевых слов) или просто полужирное начертание ([W3C:Markup](http://dev.w3.org/html5/markup/b.html), [WHATWG](http://www.whatwg.org/specs/web-apps/current-work/multipage/text-level-semantics.html#the-b-element));
- `<em>` — обозначал выделение, а сейчас обозначает _экспрессивно-эмоциональное выделение_, т.е. слово или фразу, произнесённые иначе ([W3C:Markup](http://dev.w3.org/html5/markup/em.html), [WHATWG](http://www.whatwg.org/specs/web-apps/current-work/multipage/text-level-semantics.html#the-em-element));
- `<strong>` — обозначал большее усиление экспрессии, а сейчас обозначает _высокую важность_, что, в общем, почти то же самое (ещё большее усиление или важность сейчас определяется уровнем вложенности) ([W3C:Markup](http://dev.w3.org/html5/markup/strong.html), [WHATWG](http://www.whatwg.org/specs/web-apps/current-work/multipage/text-level-semantics.html#the-strong-element)).

## Новая семантика презентационных элементов

В HTML4 элементы `<i>` и `<b>` были [презентационными](http://www.w3.org/TR/html401/present/graphics.html#h-15.2.1). Они по-прежнему могут использоваться там, где этого требует типографская традиция. Тем не менее, теперь они обрели семантику и могут быть оформлены при помощи CSS, что делает их _не только_ презентационными — элемент `<b>`, например, совсем не обязательно должен быть полужирным. Поэтому **для обозначения смысловой нагрузки элементов рекомендуется использовать классы**; это позволит легко изменить внешний вид элементов в дальнейшем.

### Элемент `<i>`

> Элемент `<i>` представляет собой фрагмент текста с дополнительным выделением или же экспрессивно-эмоциональным сдвигом относительно обычного текста (то, что обычно обозначается курсивом в типографике)
> 
> [Спецификация W3C](http://dev.w3.org/html5/markup/i.html)

Обычно обозначаются курсивом: иностранные слова (с атрибутом `lang`), таксономия и технические термины, названия кораблей, пометки в сценариях, нотное письмо, вставки размышлений или рукописного текста. Пример:

    <blockquote cite="http://www.trussel.com/bladerun.htm">
        <ol class="script semantic-list">
            <li>
                <b class="character">Декард</b>:
                Шевелись! Прочь с дороги!
            </li>
            <li class="action">
                Декард стреляет и убивает Зору
                в драматической замедленной сцене.
            </li>
            <li>
                <b class="character">Декард</b>:
                <i class="voiceover">В отчёте это будет выглядеть
                рутинным устранением двойника, что, однако, совсем
                не поможет мне чувствовать себя лучше после выстрела
                женщине в спину. И снова. Жалость где-то внутри.
                К ней, к Рэйчел.</i>
            </li>
            <li>
                <b class="character">Декард</b>:
                Декард. Б-263-54.
            </li>
        </ol>
    </blockquote>

В указанном примере элемент `<i class="voiceover">` используется для обозначения внутреннего диалога персонажа, произнесённого в другом тоне.

    <blockquote>
        <p>
            Прошлой ночью мы ели
            <i lang="ja-cyrl" title="угорь">унаги</i>,
            <i lang="ja-cyrl" title="копчёный лосось">абури-заке</i> и
            <i lang="ja-cyrl" title="осьминог">тако</i>, а все
            <i lang="ja-cyrl" title="тунец">торо</i> суши кончились.
        </p>
    </blockquote>

Элемент `<i lang="ja-cyrl">` используется в этом примере для обозначения «идиоматических фраз из другого языка» (японских слов). Полный список значений атрибута `lang` вы можете найти в [официальном списке IANA](http://www.iana.org/assignments/character-sets); или же вы можете воспользоваться замечательным [сервисом по поиску языковых обозначений от Ричарда Исиды из W3C](http://rishida.net/utils/subtags/).

    <blockquote cite="http://en.wikipedia.org/wiki/Nanotyrannus">
        <p>
            <i class="taxonomy">Nanotyrannus</i> («карликовый тиран»)
            принадлежит к семейству тиранозавров, и, возможно, является
            юной особью <i class="taxonomy">тиранозавра</i>.
            Его череп, ныне находящийся в КМЕ (Кливлендском Музее
            естествознания), был найден Чарльзом Гилмором в 1942-м
            году, описан им же в 1946-м. Гилмор обозначил его
            как представителя нового вида 
            <i class="taxonomy">Gorgosaurus lancensis</i>.
        </p>
    </blockquote>

Элементом `<i class="taxonomy">` в данном примере обозначается таксономическая единица.

Используйте `<i>` только в том случае, когда не удаётся найти ничего более подходящего: `<em>` для фрагментов с экспрессивно-эмоциональным выделением, `<strong>` для смысловой важности, `<cite>` для имён при цитировании или в библиографии, `<dfn>` для определений и `<var>` для математических переменных. Однако для придания курсивного начертания таким блокам текста, как ремарки, стихотворные строфы и цитаты, используйте CSS . Не забывайте использовать атрибут `class` для задания функциональной роли элемента — это позволит с легкостью переопределить стили в дальнейшем. К примеру, вы можете сделать выборку по атрибуту `lang` в CSS, используя селектор вида `[lang="ja-cyrl"]`.

### Элемент `<b>`

> Элемент `<b>` представляет собой фрагмент текста, который выделяется из окружающего его контекста, но не передает никакого особого значения. Это, например, ключевые слова в выдержках, названия продуктов в обзорах или другие части текста, которые по правилам типографики обычно выделяются полужирным начертанием.
> 
> [Спецификация W3C](http://dev.w3.org/html5/markup/b.html)

Для текста, обрамленного в `<b>` (который должен просто отличаться от основного), нет необходимости использовать `font-style:bold` — можно обратиться к другим стилям: скруглённому фону, большему размеру шрифта, другому цвет или особому форматированию типа капители. К примеру, в [приведенном выше отрывке](#deckard), `<b class="character">` используется для указания на того, кто говорит или рассказывает.

Текст, который набран полужирным по типографским соглашениям (а совсем **не** потому, что он более важен) может использоваться для выделения имён в голливудских сплетнях или в качестве вводного текста для сложных или оформленных в классическом стиле текстов:

    <p class="sub-versal">
        <b class="opening-phrase">Было около часу</b>,
        когда Шерлок Холмс вернулся с прогулки.
        Он держал в руках листок голубой бумаги,
        исчирканный заметками и рисунками.
    </p>

В данном примере буквица соединяется с текстом при помощи `<b class="opening-phrase">`. Для ее создания используется псевдо-элемент `:first-letter`. В этом случае открывающая фраза выделена полужирным только из оформительских соображений, но если бы этот фрагмент был семантически важен, то `<strong>` или другой подобный элемент подошли бы лучше.

    <p class="versal">
        Просматривая свои записи о приключениях Шерлока Холмса, —
        а таких записей, которые я вел на протяжении последних восьми
        лет, у меня больше семидесяти, — я нахожу в них немало
        трагических случаев, есть среди них и забавные, есть
        и причудливые, но нет ни одного заурядного.
    </p>

Несмотря на то, что мы можем использовать `<b>` для традиционного типографического оформления вроде выделения капителью первого слова, фразы или предложения, псевдо-элемент `:first-line` больше подходит для таких целей. Например, все первые абзацы [HTML5Doctor.com](http://html5doctor.com/) оформлены при помощи элегантного `:first-of-type`.

Используйте `<b>` только тогда, когда нет ничего более подходящего, например: `<strong>` для текста с семантической важностью, `<em>` для акцентированного текста (с «логическим ударением»), элементы от `<h1>` до `<h6>` для заголовков и `<mark>` для подсвеченного или выделенного текста. Для [облака тегов](http://www.whatwg.org/specs/web-apps/current-work/multipage/links.html#tag-clouds) используйте список с соответствующими классами. Для воссоздания традиционных типографских приёмов используйте [CSS-селекторы псевдо-элементов](http://www.w3.org/TR/CSS2/selector.html#pseudo-element-selectors): `:first-line` и `:first-letter`, каждый для своего случая. И ещё раз, не забывайте использовать атрибут `class` для обозначения того, зачем был использован каждый конкретный элемент  — это упростит повторное изменение элемента в дальнейшем.

## …и для сравнения: элементы `<em>` и `<strong>`

Хотя `<em>` и `<strong>` остались практически такими же, как были, в их значении всё же произошли некоторые изменения. В HTML4 они означали «акцент» и «сильный акцент». Сейчас их значение несколько видоизменилось: `<em>` обозначает _экспрессивно-эмоциональное выделение_ (т.е. нечто, произнесённое иначе), а `<strong>` обозначает важность.

### Элемент `<em>`

> Элемент `<em>` обозначает часть текста с эмфатическим ударением.
> 
> [Спецификация W3C](http://dev.w3.org/html5/markup/em.html)

Термин «ударение» имеет отношение к лингвистике. Ударение изменяет эмоциональную окраску слова, что, в свою очередь, может изменить смысл предложения. Например, фраза «Быстро позови _доктора!_» акцентирует важность того, чтобы позвали именно доктора — возможно, в ответ на чей-то вопрос «Мне позвать сестру?» Напротив, фраза «_Быстро_ позови доктора!» акцентирует важность немедленного вызова.

Используйте `<strong>` в других случаях для обозначения важности и `<i>` для курсивного начертания без эмоциональной окраски. Уровень вложенности обозначает силу акцентирования.

### Элемент `<strong>`

> Элемент `<strong>` обозначает часть текста с высокой важностью.
> 
> [Спецификация W3C](http://dev.w3.org/html5/markup/strong.html)

Добавить, в общем-то, и нечего — элемент `<strong>` хорошо всем нам знаком. Используйте вложенные элементы `<strong>` для обозначения относительной важности, `<em>` для эмафтического ударения и `<b>` для стилистически выделенных или просто полужирных фрагментов текста без подчёкнутой важности.

## Резюмируя...

И последнее: все эти элементы (как и большинство HTML5-элементов) намеренно были сделаны _медиа-независимыми_, т.е. их семантика теперь не привязана к отображению в визуальных браузерах.

Что же мы имеем? Две презентационных дворняжки из HTML4 превратились в полноценные, насыщенные смыслом HTML5-элементы, готовые снова вернуться в ваш код. Сможете ли _вы_ устоять перед их блестящими, полными семантики щенячьими глазками? Дайте нам знать!

Перевод оригинальной статьи «[The i, b, em, & strong elements](http://html5doctor.com/i-b-em-strong-element/)» [Оли Стадхольма](http://oli.jp/) (Oli Studholme), опубликованной на сайте [HTML5Doctor.com](http://html5doctor.com/).