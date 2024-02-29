# **raise**

`raise` используется для вызова исключения, что позволяет программе обработать\
ошибку или иное нежелательное событие. Это не всегда связано с `if-elif-else`,\
но может быть использовано внутри этих конструкций для управления ошибками.

```python
age = -5
if age < 0:
    raise ValueError("Возраст не может быть отрицательным!")
else:
    print("Всё гуд")    
```

Как видите, дополнительная конструкция `raise` позволяет нам обрабатывать\
как-то ожидаемые ошибки. Как и что должно произойти, что должно вывестись\
на экран, если ни одно из условий не сможет отработать и в нашей логике\
может быть какая-то ошибка. Если мы можем "предсказать", что за\
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
механизм, который как раз и называется - обработка исключений.

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
Данный список актуален для `python 3.3` и выше, в более ранних версиях\
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
            * `ZeroDivisionError` - деление на ноль.
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
        * `NotADirectoryError` - ожидалась директория, но это файл.
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
упрощения отладки

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

# **Collections.**

**Коллеции и их виды:**

Что такое коллеции в языке Python?

**Коллекции** - программный объект (**переменная-контейнер**), хранящая набор\
значений одного или различных типов, позволяющий обращаться к этим\
значениям, а также применять специальные функции и методы,\
зависящие от типа коллекции.


Наши коллекции дробятся на такие категории, как:

* **Последовательности**
* **Множества**
* **Отображения**

Все виды коллекций:

* **Список** - `list()`
* **Кортеж** - `tuple()`
* **Множество** - `set()`
* **Неизменяемое множество** - `frozenset()`
* **Словарь** - `dict()`

И так же между собой все эти категории делятся на **изменяемые** и **неизменяемые**\
коллекции.

**Изменяемые** – коллекции, которые можно изменить в любой момент\
времени.

**Неизменяемые** – коллекции, которые изменить нельзя, но можно\
пересоздать.


**Строки** тоже в какой-то степени можно считать коллекцией, т.к. они\
хранят последовательность символов. Но строки - это базовый тип, к тому\
же в коллекциях также можно хранить строки, поэтому принято их к\
коллекциям не относить

Небольшая подсказка по изменяемости и неизменяемости:

![img_13.png](https://raw.githubusercontent.com/pareikoVladislav/innoDom012/main/img_13.png)

---



![img_11.png](https://raw.githubusercontent.com/pareikoVladislav/innoDom012/main/img_11.png)

```python
my_list = [] # = list()
my_tuple = () # = tuple()
'' "" """""" ''''''
my_set = {} # не прокатит
my_frozenset = {} # так же не прокатит
my_dict = {} # = dict()
```

Давайте так же посмотрим с вами на общие свойства наших встроенных коллекций:


![img_12.png](https://raw.githubusercontent.com/pareikoVladislav/innoDom012/main/img_12.png)


Так же давайте освежим наши знания о том, что у нас за страшные термины такие:\
**изменяемость**, **индексированность** и **уникальность**:

* **Изменяемость** коллекции — позволяет добавлять в коллекцию новых членов или\
удалять их после создания коллекции.

* **Индексированность** – каждый элемент коллекции имеет свой порядковый номер —\
индекс(**НАЧИНАЕТСЯ С НУЛЯ!**). Это позволяет обращаться к элементу по его\
порядковому индексу, проводить слайсинг(**«нарезку»**) — брать часть\
коллекции выбирая исходя из их индекса.

**Уникальность** – каждый элемент коллекции может встречаться в ней только один\
раз. Это порождает требование неизменности используемых типов данных для\
каждого элемента, например, таким элементом не может быть список.

```python
my_list = ['a', 'b', 'c', 1, 4, (1, 2, 3), [1, 2, 2, 3], {"a": 1}]
my_tuple = (1, 'a')
my_set = {1, 2, 3, 4, 5, 6, 7, 8, 9}
my_dict = {
    'a': 1,
    'b': 2,
    'c': 3,
}
my_string = "My awesome string"
```

---

# **General approaches to working with any collection**

что можно делать с любой стандартной коллекцией независимо от её типа? Есть\
некоторые методы и операции, которые мы можем применять ко всем нашим коллекциям,\
будь то список, кортеж, множество, или что-то ещё(включая строку).

* Печать элементов коллекции с помощью функции `print()`

```python
print(my_list) # ['a', 'b', 'c']
print(my_tuple) # (1, 'a', ["John", "Marry", "Nick"])
print(my_set) # {1, 2, 3, 4, 5, 6, 7, 8, 9}
print(my_dict) # {'a': 1, 'b': 2, 'c': 3}
print(my_string) # My awesome string
```

* Подсчёт количества элементов коллекции с помощью функции `len()`

```python
print(len(my_list)) # 3
print(len(my_tuple)) # 3
print(len(my_set)) # 9
print(len(my_dict)) # 3
print(len(my_string)) # 17 (потому что в строках элементом является один символ, пробел так же считается.)
```

* Проверка принадлежности элемента данной коллекции c помощью оператора `in`

```python
print('a' in my_list)           # True
print('q' in my_list)           # False
print('a' not in my_list)       # False
print('q' not in my_list)       # True

print('a' in my_dict) # True - без указания метода поиск по ключам
print('a' in my_dict.keys()) # True - аналогично примеру выше
print('a' in my_dict.values()) # False - так как 'а' — ключ, не значение
print(1 in my_dict.values()) # True
```

* Обход всех элементов коллекции в цикле `for in`(больше об этом на теме циклов)

```python
for elem in my_list:
  print(elem)
```

Что ещё есть у нас из обобщённых подходов к коллекциям:

* Функции `min()`, `max()`, `sum()`

```python
new_list = [1, 2, 3, 4, 5, 6, 7, 8, 9]
print(sum(new_list))
print(min(new_list))
print(max(new_list))
```

```python
# Получение средней зп у сотрудников
employees_salary = [1000, 2500, 281, 473, 774]

try:
    average = sum(employees_salary) / len(employees_salary)
    print(f"Средняя зп: {average}")
except ZeroDivisionError:
    print("Список пуст.")
```

---

# **List**

это стандартная изменяемая коллекция, которая позволяет хранить\
различные типы данных в одном месте и под одним именем.\
Списки можно создавать с помощью слова list либо с помощью\
квадратных скобок.

Для создания списка с элементами, можно записать так: функция `list()`\
может принимать любой другой итерируемый объект:

```python
list_1 = list("hello")
list_2 = ['q', 'w', 'e', 'r', 't', 'y']
```

Благодаря динамической типизации в списках можно хранить разные\
типы данных, т.е. в одном списке одновременно можно хранить и строку,\
и число, и любой другой тип.

```python
list_values = [True, 'j', 1, "e", 2, "5", None, [1, 4, "a"], {2, 4, 5,}, {"a": 2}]
```

Выводить списки можно с помощью функции `print()`, тогда результат\
вывода является всеми элементами списка

---

Списки, как и строки, подчиняются **индексированию**

```python
new_list = list_values[:6]
new_list2 = list_values[:-1]
new_list3 = list_values[:-4]
```

Срезы также работают на списках, благодаря им можно получить новый\
список с выборкой данных по числам, передаваемых в срез

```python
new_list4 = list_values[1:5]
new_list5 = list_values[7:4:-1]
new_list6 = list_values[::1]
```

Элементы списка можно **изменять**, обратившись к ним по индексу.

```python
new_list_of_values = [1, 2, 3, 4, 5]

new_list_of_values[2] = 300
new_list_of_values[3] = "qwerty"

print(new_list_of_values)
```

Списки можно объединять с помощью оператора `+`

```python
list_val = [1, 2, 3]
list_val_str = ['4', '5', '6']

print(list_val + list_val_str)
```

Так же списки можно разложить благодаря следующему написанию переменных:

```python
new_list_example = [13, 54, 76]

a, b, c = new_list_example

print(a, b, c)
```

**Функция range()**

Функция **range(start, end, step)**, принимает три ключевых\
параметра и создаёт итерируемый объект - последовательность из чисел,\
начиная с начала `start`, не включаемого конца `end` и шага `step`

С помощью функции **range()** можно создавать списки, состоящие из\
чисел

* Когда передаётся `3` параметра, то это **начало последовательности**,\
**конец** и **шаг**.

* Когда передаётся `2` параметра, то это **начало последовательности** и\
**конец**, а **шаг** передаётся автоматически `1`

* Когда передаётся `1` параметр, то это **конец последовательности**, а\
**начало** – автоматически `0`, **шаг** – автоматически `1`

```python
range_list = list(range(0, 10, 1))
range_list_1 = list(range(7, 20))
range_list_2 = list(range(20))

print(range_list, range_list_1, range_list_2, sep="\n")
```

# **List methods**

В наших списках существуют различные методы, которые могут использоваться\
нами в различных задачах. Постараемся рассмотреть самые\
распространённые из них:

* `append()` - Добавляет элемент в конец списка

```python
numbers = [1, 2, 3]
numbers.append(4)
print(numbers)  # [1, 2, 3, 4]
```

---
есть белый список (пустой) и чёрный список гостей. В чёрном списке находится\
Дима. Он очень плохо себя показал в прошлый раз в заведении.

Напишите проверку, что если в пользовательском вводе приходит Олег - он НЕ\
должен попасть в белый список. Учтите регистр и пробелы в начале и конце ввода
---


* `extend()` - Расширяет список, добавляя элементы из другого\
итерируемого объекта

```python
numbers = [1, 2, 3]
more_numbers = [4, 5, 6]
numbers.extend(more_numbers)
print(numbers)  # [1, 2, 3, 4, 5, 6]
```

---

* `insert()` - Вставляет элемент на указанную позицию в списке

```python
fruits = ['apple', 'banana', 'cherry']
fruits.insert(1, "orange")
print(fruits)  # ['apple', 'orange', 'banana', 'cherry']
```

* `remove()` - Удаляет первое вхождение указанного элемента из списка

```python
numbers = [2, 1, 2, 3, 2, 2]
numbers.remove(2)
print(numbers)  # [1, 2, 3, 2, 2]
```

* `pop()` - Удаляет и возвращает элемент по указанному индексу

```python
fruits = ['apple', 'banana', 'cherry']
popped_fruit = fruits.pop(1)
print(popped_fruit)  # 'banana'
print(fruits)  # ['apple', 'cherry']
```

---

* `index()` - Возвращает индекс первого вхождения указанного элемента в списке

```python
numbers = [1, 2, "wah", 3, 2, ["a", "b", -1], (1, 2, 3), "wah"]
index = numbers.index("wah")
print(index)  # 2
```

* `count()` - Возвращает количество вхождений указанного элемента в списке

```python
numbers = [1, 2, 3, 2, 2, 2, 2, 2]
count = numbers.count(2)
print(count)  # 6
```

* `sort()` - Сортирует список по возрастанию

```python
numbers = ["a", "c", "b", "e"]

numbers.sort()
print(numbers)  # ['a', 'b', 'c', 'e']
```

* `reverse()` - Обращает порядок элементов в списке

```python
fruits = ['apple', 'banana', 'cherry']
fruits.reverse()
print(fruits)  # ['cherry', 'banana', 'apple']
```

```python
list1 = [1, 2, 3, 4, 5]
list2 = [4, 5, 6, 7, 8]

# Объединяем списки и удаляем дубликаты через переопределение методом set()
combined_list = list(set(list1 + list2))

print(combined_list)
```

# **Nested Lists**

это списки, которые хранятся внутри **друг друга**

Примеры создания вложенных списков, данные внутри них могут\
отличаться:

```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
```

Вложенные списки классифицируются **по глубине**. Если список внутри\
списка - это **двухмерный список** и его глубина - `2`. Если список в списке\
внутри списка - это **многомерный список** и его глубина - `3`.

```python
new_matrix = [
    [[1, 2, 3], [4, 5, 6], [7, 8, 9]],
    [[1, 2, 3], [4, 5, 6], [7, 8, 9]],
    [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
]
```

# **Tasks**
1. Пользователь вводит слова **через пробел** в одном вводе\
Во втором вводе вводит конкретное слово.

Cконвертировать первый ввод пользователя в список\
Удалить введённое слово из этого списка и вывести его отдельно в строке\
Учитывать возможные ошибки и пустой ввод

2. Пользователь вводит `n` слов через запятую в двух разных переменных (два ввода)\
Сконвертировать его ввод в списки и к первому списку добавить второй

---

# **Tuples**

**Кортеж** – это индексированная структура данных, похожая на список,\
предназначенная для безопасного извлечения и отправки данных, а также\
для безопасного их хранения

**Кортеж** – это неизменяемая коллекция, которая содержит ряд\
преимуществ:

* данные, хранящиеся в кортеже, невозможно изменить, они полностью\
защищены от “случайных” изменений;
* кортеж как структура занимает меньший вес в памяти;
* кортеж можно использовать ключом словаря.


Для создания кортежа используются **круглые скобки** либо функция\
`tuple()`

Если заключить данные просто в круглые скобки, то кортеж не будет\
создан. Для того, чтобы создать кортеж с одним элементом, нужно\
поставить после него **запятую**. Например: `(1, )` - это **кортеж**.

```python
list_ = [1, 2, 3]

my_tuple = tuple(list_)

my_tuple_1 = (4, 5, 6)
```

На кортежи действуют все методы и функции списков, которые не\
изменяют данные внутри структуры.


# **Методы Кортежей**

* `count()` - подсчитывает количество вхождений опр. значения в кортеж
* `index()` - возвращает индекс первого вхождения элемента, который\
передаётся в метод

```python
my_tuple = ()
my_tuple_1 = tuple()
```

Где наши кортежи могут применяться?

* **Обработка данных** из базы данных: Кортежи могут быть использованы для\
представления результатов запросов к базе данных. Например, при\
извлечении данных из таблицы можно использовать кортежи для хранения\
значений каждой строки. Методы, такие как `count()` и `index()`, могут\
использоваться для анализа и обработки этих данных.

* **Возвращение** нескольких значений из функции: Функции в Python могут\
возвращать кортежи в качестве результата. Например, функция, которая\
вычисляет минимальное и максимальное значение в списке, может вернуть\
кортеж из двух значений. Затем можно использовать методы кортежей,\
такие как `count()` и `index()`, для работы с этими значениями.

* **Обмен значениями переменных**: Кортежи могут быть использованы для обмена\
значениями между переменными без необходимости использования\
временной переменной.

```python
a = 1
b = 2

print(f"До обмена: a = {a}, b = {b}")

a, b = b, a

print(f"После обмена: a = {a}, b = {b}")
```

* **Кеширование результатов**: Кортежи могут быть использованы в качестве\
ключей словаря для кеширования результатов вычислений. Например, если\
у вас есть функция с дорогостоящими вычислениями, вы можете сохранять\
результаты в словаре с ключами-кортежами аргументов функции. При\
повторных вызовах функции с теми же аргументами, вы можете использовать\
сохраненные значения вместо повторных вычислений.

* **Сопоставление именованных значений**: Кортежи могут использоваться для\
сопоставления именованных значений, когда требуется более сложная структура\
данных, чем просто набор переменных. Например, можно использовать кортежи для\
представления информации о студентах, где каждый кортеж содержит имя, возраст,\
оценки и другую информацию о студенте.