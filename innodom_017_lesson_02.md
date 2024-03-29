# **Arithmetic operators in Python**

Что у нас собственно по операторам вычислений? В Питоне они следующие:

* `-` — вычитание
* `*` — умножение
* `**` — возведение в степень (а если возвести в степень 0.5, то можно получить       
квадратный корень)
* `/` — деление (при делении чисел получается float)
* `//` — целочисленное деление
* `%` — остаток от деления


Однако и тут не так всё легко, как может показаться. Так же, как и в математике,\
в Питоне есть **приоритетность** для операторов. Вот наша с вам иерархия приоритетов\
от высокого к низкому ( для операторов вычесления ):

* Возведение в степень `**`
* Деление `/` Остаток от деления `%` Умножение `*`
* Вычетание `-` Сложение `+`
* Операторы сравнения `in`, `not in`, `is`, `is not`, `<`, `<=`, `>`, `>=`, `<>`, `!=`, `==`


```python
# Сначала выполняется умножение
# потом операция сложения
# Результат: 17
5 + 4 * 3
```

Так же мы можем определять приоритет сами, взяв нужный нам кусок\
выражения в круглые скобки:

```python
# Круглые скобки () переопределяют приоритет арифметических операторов
# Вывод: 27
(5 + 4) * 3
```

Некоторые группы включают по несколько операторов python. Это значит, что все\
представители одной группы имеют один уровень приоритетности.

При наличии двух или более операторов с одинаковым уровнем в дело вступает\
ассоциативность, определяющая порядок.

Например, у операторов умножения и деления приоритетность одинаковая. В одном\
выражении тот, что находится слева, будет выполняться первым.

```python
# Тестирование ассоциативности слева направо
print(4 * 7 % 3)

print(2 * (10 % 5))
```

---

**Ассоциативность** — это порядок, в котором **Python** выполняет выражения,\
включающие несколько операторов одного уровня приоритетности.

**Неассоциативные операторы**

Наши с вами операторы сравнений не поддерживают ассоциативность. Для\
них применяются специальные правила порядка, в которых ассоциативность\
НЕ принимает участия.

Так же работает связывание операторов присваивания (например, `a=b=c`),\
а вот `a = b += c` вернет ошибку.


```python
a = q = 5
a = 1

print(a)
print(q)
print(id(a))
print(id(q))
```

---

# **Data Typing in Python**

Как мы обсуждали ранее, **Python** - язык динамический.

Всякий раз, когда мы пишем программу на **Python**, мы сталкиваемся с разными\
наборами операторов, один из которых является оператором присваивания\
( = ), в котором мы инициализируем переменную со значением.


Когда мы говорим о таких языках, как **C, C++ и Java**, память распределяется на\
основе типа данных переменной, и к ней обращаются соответственно, тогда как python\
является динамически типизированным языком, он сохраняет значение в каком-то\
месте (**в ячейке памяти**), а затем объединяет соответствующее имя\
переменной с контейнером.

Тип данных определяется во время выполнения:

```python
a = 12.0
print(type(a))
b = 24
print(type(b))
c = 'data'
print(type(c))
print(a * 3)
print(b * 3)
print(c * 3)
```

На старте мы инициализируем ( создаём ) три переменные: `a`, `b`, и `c`,\
и присваиваем им наши значения ( дробное число, целое число и строку )

Дальше мы проверяем тип данных наших переменных ( Всё благодаря методу `type()` )\
И после всего этого мы проводим одно и то же действие с нашими переменными - умножаем\
их на тройку. Но результат у нас будет разным, за счёт того, что наш Питон при\
проходе по коду определил тип данных для каждой из переменных. На выходе мы\
молучаем так же дробное число, целое число и строку.

Так же Питон поддерживает такой прекрасный синтаксический сахар ( которым пользуются\
не все к сожалению ), как определение типа переменной в момент\
её определения. Как это работает:

```python
my_int: int = 83
my_string: str = "Hello!"
my_float: float = 4.1
```

Что поменялось: теперь наша переменная имеет очевидный, присвоеный ей тип данных.

Это может помочь разработчику не запутываться в том, а что же у него в переменной\
будет / может лежать и так же предотвратить попадание в эту переменную\
какого-то другого типа данных. Это что касается сред разработки.

---

# **Data types in Python**

В Python, типы данных могут быть **изменяемыми** и **неизменяемыми**.

**Неизменяемые** типы данных означают, что значения, которые хранятся\
в таких объектах, не могут быть изменены после создания объекта.

**Изменяемые** типы данных, напротив, могут изменять значение внутри объекта.


В целом же наши данные в Python бывают:
* Базовые типы данных(статические)
* Коллекции


К базовым типам данных мы можем отнести:

* **Числовые типы данных**
   * `int`: целочисленные значения
   * `float`: числа с плавающей точкой (дробные числа)
   * `complex`: комплексные числа

* **Логический тип данных**
   * `bool`: логический тип данных

* **Строковый тип данных**
   * `str`: строки

* **NoneType**
   * `None`: тип данных, который указывает на отсутствие значения

Каждый из этих типов данных имеет свои собственные операции, которые можно\
выполнять с помощью встроенных функций и операторов языка Python.


Что же до наших более сложных структур данных?\
Наши коллекции состоят из:

* **Последовательностей** ( индексированные, элементы не уникальны )
   * Изменяемые
      * список(`list`)
   * Неизменяемые
     * строки(`str`)
     * кортежи(`tuple`)

* **Множества** ( неиндексированные, элементы уникальны )
   * Изменяемые
     * множества(`set`)
   * Неизменяемые
     * неизменные множества(`frozenset`)

* **Отображения** ( Неиндексированный набор пар <ключ: значение> )
   * словари(dict)

---

![img_10.png](https://raw.githubusercontent.com/pareikoVladislav/innoDom012/main/img_10.png)

---

Чтобы вам было проще запомнить: Изменяемые типы данных - первые буквы\
наших типов данных `List`, `Set`, `Dict` - `LSD`


# **Conclusion:**

Типы данных в Python у нас могут быть изменяемыми и неизменяемыми. К изменяемым\
у нас относятся `List`, `Set`, `Dict` ( `LSD`, не забываем ) Остальные типы данных\
у нас неизменяемые. Так же в этих типах данных у нас имеются категирии:

`Последовательности` - Это те типы данных, по которым мы можем пройтись циклом,\
у которых есть индексы.

`Множества` - типы данных, являются неиндексируемыми, значения в них являются\
уникальными.

`Отображения` - набор данных в формате `ключ: значение`


```python
# int
int_var = -9

# float
float_var_1 = -14.6
float_var_2 = float(3) # 3.0
float_var_3 = 5. # 5.0
float_var_4 = .7 # 0.7

print(float_var_1, float_var_2, float_var_3, float_var_4)
print(type(float_var_1))
print(type(float_var_2))
print(type(float_var_3))
print(type(float_var_4))
# небольшой подвох с этим типом данных
print(.6 + .6 + .6)
```

# **Working with built-in functions: input, print, type. Static data types**

Для получения информации с клавиатуры в Python есть функция `input()` У неё\
есть опциональный параметр `prompt`, который является выводимой строкой при\
вызове функции.

Когда `input()` вызывается, поток программы останавливается до тех пор,\
пока пользователь не введет данные через командную строку. Для ввода\
нужно нажать `Enter` после завершения набора текста. Обычно `Enter`\
добавляет символ новой строки `(\n)`, но не в этом случае. Введенная\
строка просто будет передана приложению.

```python
input()
input(prompt="Please, enter your value: ")
input("Please, enter your value: ")
```


По умолчанию функция `input()` конвертирует всю получаемую информацию в строку,\
как можно было убедиться из примеров выше. В этом плане, если нужно\
произвести работу с числами, нужно быть немного аккуратным и учитывать эту конвертацию.\
Что можно с этим сделать? Преобразовать наш вывод ещё в моменте вызова `input()`:


```python
float_value = float(input("Enter a number: "))
default_input_output = input("Enter a number: ")
print(type(default_input_output))
print(type(float_value))
```

Функция `type()` помогает нам узнать собственно тип данных какого-то объекта, или\
же нашей переменной:

```python
print(type(float_value))
print(type([1, 2, 3, 4, 5]))
```

Ну и последнее - наша встроенная функция `print()`. Благодаря ей мы можем выводить\
в консоль разного рода значения, которые нам интересны. Так же благодаря этой\
функции мы можем производить своего роде "дэбаг" нашего кода, когда хотим посмотреть,\
а что же нам приходит в определённую переменную и т.д.

У этой функции так же есть необязательные аргументы, некоторые из которых работают\
по дефолту, вне наших глаз:
* `sep` — Разделитель. Это может быть строка, которую необходимо вставлять между значениями,\
по умолчанию — пробел.


* `end` — Окончание вывода. Это строка, которая добавляется после последнего значения.\
По умолчанию — это перенос на новую строку `(\n)`. С помощью аргумента `end` программист\
может самостоятельно определить окончание выражения `print`.

```python
print("q", "w", "e", "r", "t", "y")
print("q", "w", "e", "r", "t", "y", sep="")
print("q", "w", "e", "r", "t", "y", sep="\n")


print("my", end="------")
print("message")
```

# **Strings.Working with strings. Literals and formatting.**

Давайте немного повторим то, что мы с вами знаем о строковом типе данных. Строки в\
`Python` - упорядоченные последовательности символов, используемые для хранения и\
представления текстовой информации, поэтому с помощью строк можно работать со всем,\
что может быть представлено в текстовой форме.

Наши с вами строки - **неизменяемый тип данных**, так как это упорядоченные\
последовательности - каждый символ в строке у нас проиндексирован ( индексаци\
начинается с нуля! ) и идёт по порядку.

Строки мы можем создать следующими путями:

```python
new_string = "my string"
new_string_2 = 'one more string'
new_string_3 = str(12334567890)
new_string_4 = """
super
string
"""

print(new_string, new_string_2, new_string_3, new_string_4, sep="\n")
print(type(new_string), type(new_string_2), type(new_string_3), type(new_string_4), sep="\n")
```

Так же не забываем, что мы можем получать отдельные символы из наших строк,\
делать по ним срезы, складывать строки, дублировать и ещё много чего.\
Давайте разбираться.

Так как наши строки являются последовательностью, они имеют индексацию\
( она начинается с нуля ) и мы можем обращаться к этим индексам:

```python
new_string = "1q2w3e4r5t6y7u"
print(len(new_string))

print(new_string[6]) # получить конкретный элемент из нашей последовательности

print(new_string[1:4]) # получить срез символов из последовательности

print(new_string[2:6])
```

При работе со срезом есть ещё и третий аргумент ( так сказать ) - шаг.\
**Шаг** - количество символов, которые мы будем пропускать в нашем срезе:

* `[::1]` - каждый первый элемент
* `[::2]` - каждый второй элемент
* `[::6]` - каждый шестой элемент
* `[::10]` - каждый десятый элемент

За счёт шага в срезе мы можем выбирать конкретные элементы в нашей строке,\
не прибегая при этом к циклам ( хотя лучше циклы ). Так же, если мы будем\
указывать шаг, который превышает по длине нашу строку - мы просто будем\
получать первый элемент:

```python
string = "qwertyqwertyqwerty"
print(string[::112])
```

Так же благодаря шагам мы можем перевернуть нашу строку:

```python
string = "qwerty"
print(string)

print(string[::-1])
```

### **Задача: Проверка наличия подстроки**

Пользователь вводит строку и подстроку.
Вывести сообщение, содержит ли введенная строка данную подстроку.


### **Задача: Проверка на палиндром**

Пользователь вводит строку.
Вывести сообщение, является ли данная строка палиндромом.

---

# **Line Literals**

Строки в апострофах и в кавычках - одно и то же. Причина наличия двух\
вариантов в том, чтобы позволить вставлять в литералы строк символы\
кавычек или апострофов, не используя экранирование:


```python
error_message = "The password field for 'testuser@gmail.com' email is empty"
warn_message = 'No updates for the "Apple INC" profile'
```

# **Shielded strings are service characters.**

* `\n` - Перевод строки.
* `\a` - Гудок встроенного в систему динамика.
* `\b` - `Backspace`, он же возврат, он же "пробел назад" – удаляет один символ\
  перед курсором. Если `\b` находится в начале строки, то удаления не происходит.
* `\r` - Возврат каретки. Возврат курсора в начало строки.
* `\t` - Горизонтальная табуляция. Горизонтальный отступ слева от начала строки.
* `\v` - Вертикальная табуляция. Вертикальный отступ сверху
* `\N{id}` - Идентификатор ID базы данных Юникода


```python
print('\N{Winking Face}')
```

```python
print("Hello\nWorld\n!\n!\n!")
```

```python
print("Hello World!!", "Hello, World!!!", sep="\b")
```

```python
print("Hello World!", "Hello World!!", "Hello World!!!", sep="\N{Winking Face}")
```


Ещё есть следующий спец символ:

* `\newline` - где `newline` продолжение строки

```python
sample_of_string = "This is a \
very \
veeeryyy \
veeeeeeeeerrrryyyyyy \
huge string!!!"
```

Относительно последнего спец символа думаю всё достаточно просто. Но выглядит не\
особо красиво, думаю согласитесь. Для решения такого запроса в `Python`\
существует так же создание гиперстрок:


```python
hyper_string = """
my
  hyper string
      and message!
"""

print(hyper_string)
```

Такие строки могут облегчить вам жизнь за счёт простоты в использовании и чтении.\
Она ничем не будет отличаться от обычной строки, разница лишь в том, что благодаря\
такому определению строк мы можем помещать большие текстовые данные, не прибегая\
при этом к `\` разделителям при необходимости.

Встречаются такие строки в технической документации к классам, функциям, файлам,\
к написанию `SLQ` запросов непосредственно в `Python`, но до этого ещё дойдём.


# **Formatting strings**

Думаю мы с вами разобрались уже со строками, тем, как же их нам определять,\
какими они могут быть, что у них есть. Но что делать, если мы хотим, чтобы часть\
строки у нас была более динамичной, чтобы значения в ней могли меняться исходя из\
каких-то событий?

Для такой работы существует как раз наше **форматирование строки**.

**Форматирование строк** - это процесс создания строки, содержащей заранее\
определенные заменители (`placeholders`), которые будут заменены на значения\
переменных или выражений во время выполнения программы. Форматирование строк\
является одним из способов создания строк в `Python` и используется для удобства\
вывода информации в консоли или в файл.

```python
user_name = input()

print("Hello," + " my name is " + user_name)
```

Существуют различные способы форматирования строк. Давайте пройдёмся от давних\
методов, которые можно встретить до сих пор, хоть и редко, до новых, которыми\
пользуются по сей день.

1) **Форматирование при помощи знака `%`**
Оператор `%` используется для замены заранее определенных заменителей на значения\
переменных или выражений:

```python
name = 'Angus'
age = 42
message = "Hello, my name is %s! I'm %d years old." % (name, age)
print(message)
```

В этом примере мы заменяем знак `%s` на строку 'Angus', а знак `%d` на число 42\
Как нам не запутаться во всех этих знаках?

Вот небольшой список возможных значений, которые мы можем подставлять к нашему проценту:


* `%d`, `%i`, `%u` - Десятичное число.
* `%o` - Число в восьмеричной системе счисления.
* `%x` - Число в шестнадцатеричной системе счисления (буквы в нижнем регистре).
* `%X` - Число в шестнадцатеричной системе счисления (буквы в верхнем регистре).
* `%e` - Число с плавающей точкой с экспонентой (экспонента в нижнем регистре).
* `%E` - Число с плавающей точкой с экспонентой (экспонента в верхнем регистре).
* `%f`, `%F` - Число с плавающей точкой (обычный формат).
* `%g` - Число с плавающей точкой. с экспонентой (экспонента в нижнем регистре),\
если она меньше, чем -4 или точности, иначе обычный формат.
* `%G` - Число с плавающей точкой. с экспонентой (экспонента в верхнем регистре),\
если она меньше, чем -4 или точности, иначе обычный формат.
* `%c` - Символ (строка из одного символа или число - код символа).
* `%r` - Строка (литерал python).
* `%s` - Строка (как обычно воспринимается пользователем).
* `%%` - Знак %.

Этот способ форматирования достаточно стар и мало где используется, хоть и используется.\
Если где-то встретите символы процента в строке - не пугайтесь и не думайте,\
что же это такое. Вы будете уже с этим знакомы.

2) **Форматирование строк при помощи метода `.format()`**

Этот метод является более новым и используется до сих пор. Достаточно практичный,\
хороший и удобный метод для работы с динамичными значениями в строках.

Часто используется при работе с какими-нибудь готовыми текстовыми шаблонами, в\
которые необходимо подставлять нужные значения только в определённые места\
( шаблонные письма для рассылок и т.д )

Давайте разбираться на практике

```python
dynamic_value = input()

print("Hello, {}".format(dynamic_value))
```

Мы так же можем передавать и несколько аргументов подряд, если необходимо:


```python
dynamic_name = input()
dynamic_age = int(input())

print("Hi! My name is {}, I'm {} y.o.".format(dynamic_name, dynamic_age))
```

Каков принцип работы нашего метода, если у нас несколько аргументов на вход?\
Если у нас фигурных скобок в шаблоновой строке больше, чем аргументов и мы не\
задавали никаких последовательностей - у нас будет ошибка, так как наш `Python`\
будет пытаться найти аргументы, которых нет.

При этом же, если у нас самих аргументов больше, чем наших фигурных скобок,\
при этом мы ничего не указывали в последовательности подставления, то `Python`\
будет брать наши аргументы по порядку для подставления, а всё, что останется\
вне наших фигурных скобок - просто проигнорируется.

Давайте разбираться:

```python
a = "Some string {} {} {} {}"

b = "One more string {} {}"

print(a.format("arg_1", "arg_2", "arg_3", "arg_4"))

print(a.format("arg_1", "arg_2", "arg_3")) # Будет ошибка, так как нам не достаёт одного аргумента для нашего шаблона

print(b.format("arg_1", "arg_2", "arg_3")) # Ошибки не будет, наш третий аргумент пропустится
```

Так же мы можем сами определять очерёдность наших аргументов:


```python
a = "{1} {0} {1}"

print(a.format("arg_1", "arg_2"))
```

Если мы сами определяем очерёдность наших аргументов, то в таком случае в целом\
мы можем указать аргументов меньше, чем их должно быть в шаблоне:

```python
b = "{0}-{1}-{0}"

print(b.format("abra", "kad"))
```

Если вдруг кому-то неудобно идти по индексам при определении последовательности наших\
аргументов - мы можем делать это через имена переменных:


```python
name = input("ENter your name: ")
age = input("ENter your age: ")

a = "Hi! My name is {name}, I'm {age} y.o."

print(a.format(name, age))
# print(a.format(name="Viktor", age=25))
```

3) **Форматирование строки через символ `f`**

Последний и актуальный, достаточно частый в использовании способ сделать нашу строку\
более гибкой - создание `f-строки`. Каков синтаксис:

```python
page_site = "VK"
status_code = 500
message = f"Can't loading '{page_site}' page. Unsecure connection."

error_message = f"Error. \nStatus code: {status_code}, \nError message: {message}"
```

# **Are f-stringers more powerful than you'd think?**

`f-строки` обладают кое-какими полезными возможностями, некоторыми особенностями, о\
которых кто-нибудь может и не знать. Разберёмся с некоторыми интересными\
возможностями `f-строк`, которые могут оказаться очень кстати в повседневной\
работе Python-программиста.

Функционал `f-строк` сравнительно недавно (начиная с `Python 3.8`) дополнен\
возможностями по выводу имён переменных вместе с их значениями:

```python
x = 10
y = 25
print(f"x = {x}, y = {y}")
# x = 10, y = 25
print(f"{x = }, {y = }")  # Лучше! (3.8+)
# x = 10, y = 25

print(f"{x = :.3f}")
# x = 10.000
```

`F-строки` поддерживают [мини-язык спецификаций форматирования](https://docs.python.org/3/library/string.html#formatspec) `Python`. Поэтому в\
модификаторы, используемые в `f-строках`, можно внедрить множество\
операций форматирования данных:

```python
text = "hello world"

# Центрирование текста:
print(f"{text:^15}")
# '  hello world  '

number = 1234567890
# Установка разделителя групп разрядов
print(f"{number:,}")
# 1,234,567,890

number = 123
# Добавление начальных нулей
print(f"{number:08}")
# 00000123
```

---

# **String methods**

У строк, как и у всех типов данных из разряда коллекций, есть свои методы.\
Давайте пройдёмся по самым распространённым из них.

* **Метод len()**
Он относится не конкретно к строкам, а скорее ко всем коллекциям. Этот\
метод просто возвращает нам длинну того, что мы поместим в него(в основном\
из коллекций).

* **Методы `lower()` и `upper()`**

Очень похожи друг на друга методы, которые предназначены для конвертации символов\
строки в верхний, или нижний регистр.

Могут пригодиться, когда вы сравниваете строковые данные и не уверены, что в них\
используется только нижний, или верхний регистр. Этими методами вы можете привести всё\
к одному единому формату.

```python
lower_string = "some string value in lower case"
print(lower_string.upper())
print(lower_string)

upper_string = "ANSJDKANSD AJSNDKAJSDUIQWE QWELQWE"
print(upper_string.lower())
```

Самые распространённые места применения таких методов на моей практике - моменты, когда\
вам нужно проверить имя пользователя. Некоторые могут вводить свои имена и фамилии с\
маленькой буквы, а некоторые с большой.

* **метод strip()** - Ещё один интересный и полезный моментами метод

Предназначен для удаления пробельных символов в начале и в конце строки. Так же зачастую\
используется при проверках имени пользователя.

```python
user_name = " Mark zukerberg "
print(len(user_name))

updated_name = user_name.lower().strip()
print(updated_name)
print(len(updated_name))
```
* **Метод split()**
Один из наиболее используемых в программировании. Этот метод может разделить строку\
на список подстрок на основе заданного разделителя (по умолчанию - пробел).

```python
my_string = "Hello, World! We're using Python!"

converted_string = my_string.split()
print(converted_string)
converted_string_2 = my_string.split(",")
print(converted_string_2)
converted_string_3 = my_string.split("e")
print(converted_string_3)
```

* **join()**
принимает в себя список со строками и конвертирует их в одну строку с\
использованием заданного разделителя.

```python
list_of_strings = ["We're", "learn", "Python", "language."]
print(", ".join(list_of_strings))
```

```python
employees_list = ["Mark", "Isabel", "Daniel", "Irina", "Margaret"]

message_template = f"""
  Dear {', '.join(employees_list)}
  You're fired.
"""
print(message_template)
```

* **Метод replace()**
Этот метод принимает в себя два аргумента: подстроку, которую вы хотите\
заменить и подстроку, НА которую вы хотите заменить. Чтобы не было путаницы в\
теории, давайте разбираться на практике:

```python
string_1 = "Hi! I'm using Java!"
print(string_1.replace("Java!", "Python!"))
print(string_1)
```

# **ord() and chr()**

Так же в Питоне есть встроенные методы, которые позволяют нам работать\
со строками в контексте преобразования символов в числа(ID этих символов)

Функция `ord()` в Python принимает строковый аргумент из одного символа\
`Unicode` и возвращает его целочисленное значение кодовой точки

```python
x = ord('A')
print(x)
print(ord('ć'))
print(ord('ç'))
print(ord('$'))
```

Функция `chr()` в Python принимает целочисленный аргумент и возвращает строку,\
представляющую символ в этой кодовой точке

```python
y = chr(65)
print(y)
print(chr(123))
print(chr(36))
```

Поскольку функция `chr()` принимает целочисленный аргумент и преобразует\
его в символ, существует допустимый диапазон для ввода.

Допустимый диапазон для аргумента – от `0` до `1114111` (0x10FFFF в\
шестнадцатеричном формате). Если входное целое число находится за пределами\
этого диапазона, будет вызвано исключение `ValueError`


```python
print(chr(-1))
# ->> ValueError: chr() arg not in range(0x110000)
```

---

Ещё некоторые методы, которые могут встречаться, или понабодиться:

* `isalnum()` - проверяет, состоит ли строка только из букв и цифр
* `isalpha()` - проверяет, все ли символы в строке - часть алфавита.\
Возвращает `bool` значение.
* `isdigit()` - проверяет, состоит ли строка только из цифр. Учитывает
так же Юникод цифры. Возвращает `bool` значение.
* `title()` - преобразовывает строку таким образом, чтобы первая буква\
каждого слова была заглавной.
* `capitalize()` - преобразовывает строку таким образом, что первая подстрока\
будет начинаться с заглавной буквы.
* `isascii()` - содержит ли строка только символы `ASCII` (**American Standard\
Code for Information Interchange**). `ASCII` — это стандартный набор символов,\
который включает в себя буквы английского алфавита (прописные и строчные),\
цифры, знаки пунктуации и некоторые специальные символы.
* `encode()` - используется для преобразования строки в последовательность байтов,\
используя определенное кодирование (`encoding`). Кодирование определяет, как\
символы будут представлены в виде байтовых значений.


Метод `encode()` полезен, когда требуется преобразовать строку в байтовую последовательность\
для передачи или сохранения данных, особенно при работе с сетевыми протоколами или файлами.\
Необходимо убедиться, что используемое кодирование соответствует ожиданиям и типу данных,\
с которыми идёт работа.

---

### **Задача: Разделение строки**

Пользователь вводит строку, содержащую имена, разделенные запятыми.
Разделить строку на список имен.
Вывести список имен.

### **Задача: Замена символов**

Пользователь вводит строку, какой-то символ на замену и символ,                       
которым нужно заменить.                          
Заменить все вхождения одного символа в строке на другой символ.
Вывести измененную строку.

### **Задача: Форматирование имени**

Пользователь вводит свое имя.

Преобразовать первую букву имени в верхний регистр и остальные       
буквы в нижний регистр. Учесть возможные пробелы в начале и конце имени

Вывести отформатированное имя.


### **Задача: Объединение строк**

Пользователь вводит две строки.
Объедините строки в одну, добавив пробел между ними.(всеми возможными способами)
Вывести объединенную строку.


### **Задача: Проверка на число**

Пользователь вводит строку.
Проверить, является ли введенное значение числовым.
Вывести сообщение о результате проверки.


### **Задача: Поиск индекса подстроки**

Пользователь вводит строку и подстроку.
Найти индекс первого вхождения подстроки в строку.


### **Задача: Проверка на уникальность**

Пользователь вводит строку.
Проверить, явлются ли символы в ней уникальными.
Вывести сообщение о результате проверки.
