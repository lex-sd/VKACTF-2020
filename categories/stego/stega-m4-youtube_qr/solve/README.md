## Голос из космоса

| Событие | Название | Категория | Стоимость |
|:--------|:---------|:----------|----------:|
| VKA-CTF`2020 | Безумие | Стеганография  | КМБ |


### Описание
> Автор: WaffeSoul
> "Я уже говорил тебе, что такое безумие? А? Безумие — это точное повторение одного и того же действия. Раз за разом… в надежде… на изменение. Это… есть… безумие."

© Ваас Монтенегро

А какая у вас ассоциация к слову "Армия"?

Мы даже попытаемся убедить тех, кто еще не познал этого. Вот вам [видео](https://youtu.be/reqO8ue4Gw0)даже попытаемся убедить тех, кто еще не познал этого. Вот вам [видео](https://youtu.be/reqO8ue4Gw0). Не бойтесь, 25го кадра там нет...

### Решение 

Есть несколько решений этого зданий.
1. Внимательно смотреть видео 10 часов, чтоб найти на 7.50.59 qr.
2.  ИЛИ Разбить видео на кадры, посмотреть хеш-сумму всех файлов. У qr будет 1 индивидуальный хеш в отличие от остальных, так как видео зациклено.( не работает если разбивать ffmpeg).
3. ИЛИ Разбить видео на кадры, отсортировать по размеру, в первых 10 кадра будет qr( на линух, кадр меньшего размера, на винде максимального).
4. ИЛИ Написать прогу, каторая будет искать статистический алгоритм, либо сканер qr.
Расшифровываем qr получаем:
``` Мой поздравление ты нашел флаг, надеюсь, ты не смотрел все 10 часов, ну лан ты ждешь флаг так вот он vka{10_h0ur5_0f_m4rch1n6_15_4n_4rmy_cl4551c}```

**Флаг:**

>vka{10_h0ur5_0f_m4rch1n6_15_4n_4rmy_cl4551c}