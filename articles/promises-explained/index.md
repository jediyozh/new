---
date: "TODO"
title: "Промисы на примерах из жизни"
---

# Промисы на примерах из жизни

Поговорим о промисах простыми словами

*Перевод «[JavaScript: Promises explained with simple real life analogies](https://codeburst.io/javascript-promises-explained-with-simple-real-life-analogies-dd6908092138)» Шрути Капур.*

![Ай промис, фото [Бена Уайта](https://unsplash.com/photos/tX4-tYibILg).](https://cdn-images-1.medium.com/max/11402/1*ycoN6Jf7xaaSnAi0S9TYmQ.jpeg)*Ай промис, фото [Бена Уайта](https://unsplash.com/photos/tX4-tYibILg).*

## Промисы простыми словами

Представьте это как разговор между двумя людьми:
> **Алекс**: Эй, мистер Промис! Можешь сбегать в магазин и принести мне itemA для блюда, которое мы приготовим сегодня вечером?
> **Промис**: Отличная мысль!
> **Алекс**: Пока ты бегаешь, я подготовлю itemB (асинхронная операция). Только обязательно скажи, нашел ли ты itemA (возвращаемое промисом значение).
> **Промис: **А если тебя не будет дома, когда я вернусь?
> **Алекс: **Тогда отправь мне смску, что ты вернулся и принесitem для меня (успешный колбэк). Если ты не найдешь, позвони мне немедленно (неуспешный колбэк).
> **Промис:** Отлично! Увидимся позже!

Проще говоря, объект promise—это данные, возвращаемые асинхронной функцией. Это может бытьresolve, если функция прошла успешно или reject, если функция вернула ошибку.

## Определение

Промис — это объект, представляющий окончательное завершение или сбой асинхронной операции. По сути, промис — это возвращаемый объект, к которому прикрепляется колбэк, вместо его передачи в функцию.

## Промис в JS

Давайте сначала поговорим о *JavaScript* и его параллелизме. *JavaScript* является однопоточным. Всё происходит в той последовательности, в которой написано, но асинхронные операции происходят в порядке их завершения.

Что, по вашему мнению, выведется в консоль в следующем примере?

    console.log('1');
    setTimeout(function(){ console.log('2'); }, 3000);

    console.log('3');
    setTimeout(function(){ console.log('4'); }, 1000);

Результатом будет 1 3 4 2. Вы можете задаться вопросом, почему 4 встречается раньше чем 2. Причина в том, что, несмотря на то, что строка с 2 описана раньше, она начала выполняться только после 3000 мс, поэтому 4 выводится до 2.

В типичном веб-приложении может выполняться множество асинхронных операций, таких как загрузка изображений, получение данных из *JSON*, обращение к *API* и других.

Теперь рассмотрим, как создать промис в *JavaScript*:

    var promise = new Promise(function(resolve, reject) {
      // Делаем, что-то, возможно асинхронное, тогда…

      if (/* Всё прошло отлично */) {
        resolve('Сработало!');
      }
      else {
        reject(Error('Сломалось'));
      }
    });

Конструктор Promise принимает один аргумент: колбэк с двумя параметрами — resolve и reject. Этот промис может быть использован следующим образом:

    promise.then(function(result) {
      console.log('Промис сработал');
    }, function(err) {
      console.log('Что-то сломалось');
    });

Если промис прошёл успешно, будет выполнен resolve, и консоль выведет Промис сработал, в противном случае выведется Что-то сломалось. Это состояние до получения resolveили reject называется состоянием ожидания, pending. Таким образом, есть три состояния промиса:

1. Ожидание ответа: pending

1. Успешное выполнение: resolve

1. Выход ошибкой: reject

![Промис успешно выполнился, [фото Скотта Вебба](https://www.pexels.com/photo/man-couple-love-people-136402/).](https://cdn-images-1.medium.com/max/8576/1*FX8c_5NxTkNo7NyEkWsjSQ.jpeg)*Промис успешно выполнился, [фото Скотта Вебба](https://www.pexels.com/photo/man-couple-love-people-136402/).*

## Пример

Чтобы полностью понять концепцию промисов, создадим приложение, которое загрузит изображение. Если изображение загружено, оно будет отображено, иначе будет выводится ошибка.

Сначала создадим promise с XMLHttpRequest:

    const loadImage = url => {
      return new Promise(function(resolve, reject) {
        // Открываем новый XHR
        var request = new XMLHttpRequest();
        request.open('GET', url);

        // После загрузки запроса
        // проверяем, был ли он успешным
        request.onload = function() {
          if (request.status === 200) {
            // Если успешный, то резолвим промис
            resolve(request.response);
          } else {
            // Если нет, то реджектим промис
            reject(Error(
              'Произошла ошибка. Код ошибки:' + request.statusText
            ));
          }
        };

        request.send();
      });
    };

Теперь, когда изображение успешно загружено, promise вернет resolve с ответом от *XHR*. Давайте используем этот promise, вызвав функцию loadImage.

    const embedImage = url => {
      loadImage(url).then(function(result) {
          const img = new Image();
          var imageURL = window.URL.createObjectURL(result);
          img.src = imageURL;
          document.querySelector('body').appendChild(img);
        },
        function(err) {
          console.log(err);
        });
    }

Мы сделали это! Неплохо, да?

А теперь сделай несколько промисов сам! Давай :)

### Дополнительные материалы

Вот некоторые статьи, которые показались мне очень полезным в процессе обучения:

1. [Статья про промисы на MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)

1. [Введение на Google Developers](http://https//developers.google.com/web/fundamentals/primers/promises)

1. [Про concurrency model на MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop#Run-to-completion)