## CryptoGirl

| Событие | Название | Категория | Сложность |
|:--------|:---------|:----------|----------:|
| VKA-CTF`2020 | CryptoGirl | Криптография | КМБ |

### Описание
> Девушка: Как же ты достал все время пропадать на службе! Выбирай! Я **ИЛИ** твоя служба  
Парень: Может быть ты хотела сказать "ты **ИСКЛЮЧАЮЩЕЕ ИЛИ** служба"  
Девушка: Все! Я ухожу от тебя!

### Решение 

В первую очередь изучаем исходный код алгоритма шифрования.  
Исходя из этой функции делаем вывод, что при шифровании используется метод [LCG](https://ru.wikipedia.org/wiki/Линейный_конгруэнтный_метод)  

```python
def next_number(m, a, c, x):
	return (a*x + c) % m
```

Метод не безопасен. Достаточно знать определенную последовательность чисел и мы сможем восстановить весь файл.

Исходя из расширения файла **PNG** можем предположить первые 16 байт исходного файла  
```python
'\x89\x50\x4e\x47\x0d\x0a\x1a\x0a\x00\x00\x00\x0d\x49\x48\x44\x52'
```

Используя операцию **xor** восстановим первые 4 числа последовательности

```python
x0 = 0x89504e47 ^ bytes_to_long(enc[0])
x1 = 0x0d0a1a0a ^ bytes_to_long(enc[1])
x2 = 0x0000000d ^ bytes_to_long(enc[2])
x3 = 0x49484452 ^ bytes_to_long(enc[3])
states = [x0, x1, x2, x3]
```

Исходя из исходного кода, нам известен модуль, по которой формируется последовательность. 
Для расшифровки файла также необходимо узнать множитель и инкремент.

В приведенной [статье](https://www.tailcall.net/blog/cracking-randomness-lcgs/) описан алгоритм восстановления оставшихся параметров.

Воспользовавшимся ими, пробуем восстановить весь файл. В результате чего получаем изображение с флагом.

**Флаг:** 

> vka{1_c4n7_7h1nk_0f_4_fl46_f0r_4n_4rmy_61rl}