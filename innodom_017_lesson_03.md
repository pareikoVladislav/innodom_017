<!-- TOC -->
* [**Formatting strings**](#formatting-strings)
  * [**.format()**](#format)
* [**Are f-stringers more powerful than you'd think?**](#are-f-stringers-more-powerful-than-youd-think)
* [**String methods**](#string-methods)
* [**ord() and chr()**](#ord-and-chr)
* [**Basic constructions**](#basic-constructions)
* [**Comparison operators**](#comparison-operators)
* [**Logical operators:**](#logical-operators)
* [**Branching operators**](#branching-operators)
* [**Conditional Operators:**](#conditional-operators)
* [**raise**](#raise)
* [**try - except**](#try---except)
* [**HomeWork**](#homework)
<!-- TOC -->

# **Formatting strings**

## **.format()**

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

emp_list_to_string = '\n'.join(employees_list)

message_template = f"""
Dear employes:

{emp_list_to_string}


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

# **Basic constructions**

# **Comparison operators**

**Операторы сравнения** - это операторы, которые сравнивают между собой\
два значения и возвращающие результат типа `bool` ( **True** \ **False** ).


**Сравнивать можно:**
* **логический тип**
* **строки**
* **числа**
* **переменную на пустоту**

**Со строками при этом есть интересная особенность при сравнениях:**

```python
"qwe" < "qwer"
```

В Python при сравнении строк сравнение происходит **лексикографически**,\
то есть сравниваются символы на соответствующих позициях в строках\
поочередно, начиная с первого символа. Если символы на одной позиции\
равны, то сравниваются следующие символы, и так далее, пока не будет\
найдено различие или одна из строк не закончится.

**В нашем примере:**

"`q`" сравнивается с "`q`" - **они равны**.\
Затем "`w`" сравнивается с "`w`" - **они тоже равны**.\
После сравниваются `e` и `e` - всё ещё проходит равенство.

На этом этапе одна из строк, "`qwe`", заканчивается, но другая строка,\
"`qwer`", еще не закончилась.

Так как до этого момента все символы совпали, **Python** продолжит сравнение,\
и так как "`qwer`" еще имеет символы, она считается большей, чем "`qwe`".\
Поэтому выражение "`qwe`" < "`qwer`" вернет значение `True`.

То есть, при сравнении строк в **Python**, длина строк имеет значение только в\
случае, если все символы на соответствующих позициях равны.

```python
"abcd" < "abce"
```

```python
True == False
"qwe" == "QWE"
25 >= 24.4
```

---

**Какие операторы сравнения бывают:**

* `>` - Проверяет, больше ли левое выражение. Если да - `True`, если нет - `False`
* `<` - Проверяет, меньше ли левое выражение. Если да - `True`, если нет - `False`
* `>=` - Проверяет, больше или равно левое выражение относительно правого.\
Если да - `True`, если нет - `False`
* `<=` - Проверяет, меньше или равно левое выражение относительно правого.\
Если да - `True`, если нет - `False`
* `==` - Проверяет равны ли выражения. Если да - `True`, если нет - `False`
* `!=` - Проверяет равны ли выражения. Если нет - `True`, если да - `False`

---

# **Logical operators:**

Логические операторы используются для выполнения логических операций, таких\
как **сравнение значений** и **комбинирование условий**.

**Какие операторы у нас имеются:**

* `not` - Логический оператор "не"
* `and` - логическое "И". Используется, когда нам нужно проверить несколько\
значений сразу. Логическое "И" запинается на лжи ( если хоть одно из условий\
`False`, вернёт `False`. Если оба значения `False`, просто вернёт\
последнее значение `False` )
* `or` - Логическое "Или". Так же используется, когда нам нужно проверить несколько\
значений сразу. Логическое "Или" запинается на правде ( если хоть одно из значений\
`True` - вернёт `True`. Если оба значения `True`, или `False` - вернёт\
последнее значение )


**Где мы можем применять эти операторы:**

* **Условные операторы**: часто используются в условных операторах, таких как\
`if`, `elif` и `else`, для проверки условий и принятия решений на основе результата.
* **Циклы**: также наши операторы могут использоваться в циклах, таких как\
`while` и `for`, для проверки условий продолжения выполнения цикла.
* **Функции и выражения**: Логические операторы также могут использоваться в функциях\
и выражениях для создания булевых (логических) значений. Например, операторы\
`and`, `or` и `not` могут быть использованы для комбинирования и инвертирования\
булевых значений и выполнения различных операций на основе этих значений.

  
**Операторы принадлежности**

**Операторы принадлежности** в Python используются в различных контекстах\
для проверки условий

* `is` - используется для проверки, указывает ли один объект на тот же участок\
памяти, что и другой объект. Он сравнивает идентичность объектов, а не их значения.
* `in` - Проверяет, принадлежность элемента x к последовательности \ коллекции\
(Находится ли подстрока в общей строке, находится ли какой-то ключ в словаре и т.д.)
* `not in` - является отрицанием оператора `in`. Он используется для проверки\
отсутствия элемента в коллекции или последовательности. Он возвращает `True`,\
если элемент отсутствует, и `False` в противном случае.

Операторы `is`, `in` и `not in` позволяют выполнять проверки на идентичность\
объектов и принадлежность элементов к коллекциям или последовательностям в `Python`:


1) **Спросите у пользователя слово и проверьте, содержится ли буква "а"**\
**в этом слове.**
2) **Запросите у пользователя список товаров, разделенных запятой, и**\
**проверьте, входит ли "молоко" в этот список.**

# **Branching operators**

**Операторы ветвлений** используются для принятия решений в программе на\
основе условий. Они позволяют программе выполнить определенные блоки кода\
только при выполнении определенных условий, что делает программу\
более гибкой и адаптивной.

Они могут встречаться в различных областях разработки, вот несколько примеров:


* **Управление потоком программы**: Операторы ветвления позволяют контролировать\
поток выполнения программы, определяя, какие части кода будут выполнены в\
зависимости от условий. Например, в зависимости от значения переменной можно\
выполнить определенные действия или перейти к другому блоку кода.

* **Обработка ошибок**: Так же можно использовать наши операторы для обработки\
исключений и ошибок в программе. Они позволяют определить, какая часть кода будет\
выполнена при возникновении определенной ошибки, и принять соответствующие\
меры для ее обработки.

* **Валидация пользовательского ввода**: проверка и валидация введенных пользователем\
данных. Например, мы можем проверить, является ли введенное значение числом\
или строкой, и выполнить различные действия в зависимости от результата.


По ветвлениям мы можем выделить две основные группы наших операторов:

* **Условные операторы**
* **Обработчики ошибок**

**Давайте по порядку**

---

# **Conditional Operators:**

* `if` - позволяет выполнить определенный набор инструкций в зависимости от\
некоторого условия. Если условие верно, выполняется блок кода, который\
определён внутри этого условия. Иначе этот блок кода пропустится.

**Как это работает:**

```
if условие:
    инструкция_1
    инструкция_2
    ...
    инструкция_n
```

После оператора `if` записывается выражение. Если это выражение истинно, то\
выполняются инструкции, определяемые данным оператором. Выражение является\
истинным, если его результатом является число не равное нулю, непустой объект,\
либо логическое True. После выражения нужно поставить двоеточие “:”

```python
user_input = int(input("Enter your age: "))

if user_input and user_input > 18:
  print("Вы совершеннолетний!")
```

* `if – else` - Используется для выполнения одного блока кода, если условие\
истинно, и другого блока кода, если условие ложно.

Бывают случаи, когда необходимо предусмотреть альтернативный вариант выполнения\
программы. Т.е. при истинном условии нужно выполнить один набор инструкций,\
при ложном – другой. Для этого используется конструкция `if – else`

```
if выражение:
    инструкция_1
    инструкция_2
    ...
    инструкция_n
else:
    инструкция_a
    инструкция_b
    ...
    инструкция_x
```

Условие такого вида можно записать в строчку, в таком случае оно будет\
представлять собой [тернарное выражение](https://ru.wikipedia.org/wiki/%D0%A2%D0%B5%D1%80%D0%BD%D0%B0%D1%80%D0%BD%D0%B0%D1%8F_%D1%83%D1%81%D0%BB%D0%BE%D0%B2%D0%BD%D0%B0%D1%8F_%D0%BE%D0%BF%D0%B5%D1%80%D0%B0%D1%86%D0%B8%D1%8F)

```python
b = True if 15 > 10 else False
print(b)
```

```python
user_input = int(input("Enter your age: "))

if user_input and user_input > 18:
  print("Вы совершеннолетний!")
else:
    print("Вы ещё слишком маленький!")
```

```python
grade = 85
if grade >= 90:
    print("Отлично!")
elif grade >= 70:
    print("Хорошо!")
else:
    print("Плохо.")
```

```python
user_input_1 = int(input("Enter the number: "))

if user_input_1 and user_input_1 <= 10:
  print(user_input_1 ** 2)
else:
  print("Something went wrong")
```

```python
b = "NO" if 15 < 10 else "YES" # тернарный оператор
print(b)
```

* `if – elif – else` - Можно использовать для реализации выбора из\
нескольких альтернатив


```python
a = int(input("введите число:"))
if a < 0:
   print("Neg")
elif a == 0:
   print("Zero")
else:
   print("Pos")
```

```python
us_account = ("Vladislav", -8749113157394717377) # superkiller2003

username = input("Enter your name: ")
us_password = input("Enter your password: ")

if username and us_password:
    if username == us_account[0]:
        if hash(us_password) == us_account[1]:
            print(f"Welcome, {username}!")
        else:
            print("Wrong password")
    else:
        print(f"User '{username}' doesn't exist")
else:
    print("You must provide your name and password")
```

1) **Запросите у пользователя два числа и проверьте, какое из них больше.**
2) **Спросите у пользователя его возраст и проверьте, может ли он получить**
**водительские права (предположим, что минимальный возраст – 18 лет).**
3) **Запросите у пользователя пароль и проверьте его длину. Если пароль**\
**короче 8 символов, выведите ошибку.**
4) **Запросите у пользователя строку и проверьте, пуста ли она.**
5) **Спросите у пользователя его имя и проверьте, начинается ли оно с буквы "А".**
6) **Запросите у пользователя два числа. Проверьте, является ли хотя бы**\
**одно из них четным.**
7) **Запросите у пользователя число и проверьте, находится ли оно в**\
**диапазоне от 10 до 50 и является ли оно четным одновременно.**
8) **Запросите у пользователя число и проверьте, является ли оно**\
**положительным, отрицательным или равным нулю.**


# **raise**

`raise` используется для вызова исключения, что позволяет программе обработать\
ошибку или иное нежелательное событие. Это не всегда связано с `if-elif-else`,\
но может быть использовано внутри этих конструкций для управления ошибками.
                                        
```python
age = -5
if age >= 0:
    print("Возраст положительный")
else:
    raise ValueError("Возраст не может быть отрицательным!")
```

**Немного примеров**

```python
is_raining = False

if is_raining:
    print("Возьмите зонтик")
else:
    raise ValueError("Зонтик не нужен")
```

Как видите, дополнительная конструкция `raise` позволяет нам обрабатывать\
как-то ожидаемые ошибки. Как и что должно произойти, что должно вывестись\
на экран, если ни одно из условий не сможет отработать и в нашей логике\
в теории может быть какая-то ошибка. Если мы можем "предсказать", что за\
ошибка будет в нашем коде - мы можем её прописать и в скобках вывести какое-то\
более подробное описание этой ошибки.


Для работы с ошибками в языке Python существует более удобная конструкция, которая\
как раз и предназначена именно для этой работы.

---


# **try - except**

**Обработчики исключений**

Исключениями (**exceptions**) в языках программирования называют проблемы,\
возникающие в ходе выполнения программы. Типичным примером исключения является\
деление на ноль, попытка вычислений между разными типами данных, невозможность\
считать данные из устройства, отсутствие доступной памяти, доступ к\
закрытой области памяти и т.п.

Для обработки таких ситуаций, как правило, предусматривается специальный\
механизм, который как раз и называется обработка исключений.

Такая конструкция определяется как `try - expect`

```python
a = [1, 2, 3]

try:
  print(a / 8)
except TypeError:
  print("Нельзя производить математические операции между категорически разными типами данных")
```

Рассмотрим иерархию встроенных в python исключений, хотя иногда вам могут\
встретиться и другие, так как программисты могут создавать собственные исключения.\
Данный список актуален для python 3.3 и выше, в более ранних версиях\
есть незначительные изменения:

* `BaseException` - базовое исключение, от которого берут начало все остальные
    * `SystemExit` - исключение, порождаемое функцией `sys.exit`при выходе из программы.
    * `KeyboardInterrupt` - порождается при прерывании программы пользователем\
    (обычно сочетанием клавиш `Ctrl+C`).
    * `GeneratorExit` - порождается при вызове метода `close` объекта `generator`.
    * `Exception` - а вот тут уже заканчиваются полностью системные исключения\
    (которые лучше не трогать) и начинаются обыкновенные, с которыми можно работать.

        * `StopIteration` - порождается встроенной функцией next, если в\
        итераторе больше нет элементов.
        * `ArithmeticError` - арифметическая ошибка
            * `FloatingPointError` - порождается при неудачном выполнении операции\
            с плавающей запятой. На практике встречается нечасто.
            * `OverflowError` - возникает, когда результат арифметической операции слишком\
            велик для представления. Не появляется при обычной работе с целыми числами\
            (так как python поддерживает длинные числа), но может возникать в\
            некоторых других случаях.
            * `ZeroDivisionError` - деление на ноль
        * `AssertionError` - выражение в функции `assert` ложно.
        * `AttributeError` - объект не имеет данного атрибута (значения или метода).
        * `BufferError` - операция, связанная с буфером, не может быть выполнена.
        * `EOFError` - функция наткнулась на конец файла и не смогла прочитать то, что хотела.
        * `ImportError` - не удалось импортирование модуля или его атрибута.
        * `LookupError` - некорректный индекс или ключ.
            * `IndexError` - индекс не входит в диапазон элементов.
            * `KeyError` - несуществующий ключ (в словаре, множестве или другом объекте).
        * `MemoryError` - недостаточно памяти.
        * `NameError` - не найдено переменной с таким именем
            * `UnboundLocalError` - сделана ссылка на локальную переменную в функции,\
            но переменная не определена ранее.
        * `OSError` - ошибка, связанная с системой
        * `ChildProcessError` - неудача при операции с дочерним процессом.
        * `ConnectionError` - базовый класс для исключений, связанных с подключениями
            * `BrokenPipeError`
            * `ConnectionAbortedError`
            * `ConnectionRefusedError`
            * `ConnectionResetError`
        * `FileExistsError` - попытка создания файла или директории, которая уже существует.
        * `FileNotFoundError` - файл или директория не существует.
        * `InterruptedError` - системный вызов прерван входящим сигналом.
        * `IsADirectoryError` - ожидался файл, но это директория.
        * `NotADirectoryError` - ожидалась директория, но это файл
        * `PermissionError` - не хватает прав доступа.
        * `ProcessLookupError` - указанного процесса не существует.
        * `TimeoutError` - закончилось время ожидания.
    * `ReferenceError` - попытка доступа к атрибуту со слабой ссылкой.
    * `RuntimeError` - возникает, когда исключение не попадает ни под одну из\
    других категорий.
    * `NotImplementedError` - возникает, когда абстрактные методы класса требуют\
    переопределения в дочерних классах.
    * `SyntaxError` - синтаксическая ошибка
        * `IndentationError` - неправильные отступы
            * `TabError` - смешивание в отступах табуляции и пробелов
    * `SystemError` - внутренняя ошибка.
    * `TypeError` - операция применена к объекту несоответствующего типа.
    * `ValueError` - функция получает аргумент правильного типа, но некорректного значения.
    * `UnicodeError` - ошибка, связанная с кодированием / раскодированием unicode в строках
        * `UnicodeEncodeError` - исключение, связанное с кодированием unicode.
        * `UnicodeDecodeError` - исключение, связанное с декодированием unicode.
        * `UnicodeTranslateError` - исключение, связанное с переводом unicode.
    * `Warning` - предупреждение.

---

**Как это всё может выглядить и каков порядок?**

```python
try:
    k = 1 / 0
except ZeroDivisionError:
    print("You can't divide numbers by zero")
```

В блоке `try` мы выполняем инструкцию, которая может породить исключение,\
а в блоке `except` мы перехватываем их. При этом перехватываются как само\
исключение, так и его потомки. Например, перехватывая `ArithmeticError`,\
мы также перехватываем `FloatingPointError`, `OverflowError` и `ZeroDivisionError`

Также возможна инструкция `except` без аргументов, которая перехватывает вообще всё\
(и прерывание с клавиатуры, и системный выход и т. д.). Но в такой форме инструкция\
`except` практически не используется, потому что у вас не будет никакой конкретики\
какой конкретно природы ошибку поймал ваш обработчик. Вместо этого используется\
`except Exception`. Однако чаще всего перехватывают исключения по одному, для\
упрощения отладки (вдруг вы ещё другую ошибку сделаете, а `except` её перехватит)

```python
my_list = [1, 2, 3, 4, 5]

try:
    result = int("not_an_integer")
    value = my_list[result]
except Exception:
    print("Произошла ошибка при доступе к элементу списка")
```

**Как делать более правильно:**

```python
my_list = [1, 2, 3, 4, 5]

try:
    index = int(input("Enter a number: "))

    try:
        result = my_list[index]
        print(result)
    except IndexError:
        print("Произошла ошибка при доступе к несуществующему индексу списка")

except ValueError:
    print("Произошла ошибка при преобразовании строки в число")
```

**Или же так:**

```python
my_list = [1, 2, 3, 4, 5]

try:
    index = int(input("Enter a number: "))
    result = my_list[index]
    print(result)
except IndexError:
    print("Произошла ошибка при доступе к несуществующему индексу списка")

except ValueError:
    print("Произошла ошибка при преобразовании строки в число")
```

Ещё две инструкции, относящиеся к нашей теме, это `finally` и `else`.\
`Finally` выполняет блок инструкций в любом случае, было ли исключение, или нет\
(применима, когда нужно непременно что-то сделать, к примеру, закрыть файл).\
Инструкция `else` выполняется в том случае, если исключения не было.


```python
try:
  user_input = int(input("Enter any number: "))
  a = user_input ** 2
  print(a)
except Exception:
  print("Переменная 'user_input' - не число. Выходим.")
else:
  print(f"Всё хорошо, результат = {a}")
finally:
  print('Я всегда выполнюсь в конце, пока!')
# Именно в таком порядке: try, группа except, затем else, и только потом finally.
```

---

# **HomeWork**

**or:**\
Создайте программу, которая проверяет, является ли число кратным 3 или 5.

**Проверка пароля:**\
Напишите программу, которая запрашивает у пользователя\
пароль. Если пароль равен "secret", выведите "Доступ разрешен", в\
противном случае выведите "Доступ запрещен".


**Проверка числа на четность:**\
Попросите пользователя ввести целое число. Если число четное,\
выведите "Число четное", иначе выведите "Число нечетное".


**Калькулятор для двух чисел:**\
Запросите у пользователя два числа и оператор (+, -, *, /). Выполните\
соответствующее математическое действие и выведите результат.\
Обработайте случай деления на ноль.


**Оценка студента:**\
Введите оценку студента от 0 до 100. Если оценка больше или равна 90,\
выведите "Отлично". Если оценка больше или равна 70, выведите\
"Хорошо". В противном случае выведите "Плохо".


**Проверка года на високосность:**\
Запросите у пользователя год. Проверьте, является ли этот год\
високосным, и выведите соответствующее сообщение.

Год високосный, если он делится на 4, но не делится на 100,\
за исключением случаев, когда он делится на 400\



**Расчет стоимости билета:**\
Попросите пользователя ввести возраст и тип билета ("детский",\
"взрослый", "пенсионер"). Рассчитайте стоимость билета с учетом
скидок (50% скидка для детей и пенсионеров)


**Определение времени суток:**\
Попросите пользователя ввести текущее время (HH:MM).\
Выведите сообщение, соответствующее времени суток:\
"Утро", "День", "Вечер", "Ночь".


**Расчет налога на доход:**\
Введите годовой доход пользователя. Рассчитайте налог на\
доход с учетом ставок: до $10,000 - 10%, от $10,000 до\
$50,000 - 20%, свыше $50,000 - 30%.


**Проверка на принадлежность к диапазону чисел:**\
Попросите пользователя ввести число. Проверьте, принадлежит ли\
число диапазону от 10 до 20 включительно.


**Калькулятор BMI (Индекс массы тела):**\
Запросите у пользователя его вес (кг) и рост (м). Рассчитайте\
его BMI по формуле BMI = вес / (рост^2) и выведите сообщение,\
указывающее на его состояние: "Недостаточный вес",\
"Норма", "Избыточный вес", "Ожирение".


**Конвертер температуры:**\
Попросите пользователя ввести температуру в градусах Цельсия.\
Затем спросите, в какую шкалу он хочет конвертировать\
(Фаренгейт или Кельвин). Выполните конвертацию и\
выведите результат.
