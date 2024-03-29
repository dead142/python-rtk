# Basic Data Types in Python
### Целые (Integers)
В Python 3 фактически нет ограничений на длину целочисленного значения. Конечно, он ограничен объемом памяти, который есть в вашей системе, как и все, но кроме этого целое число может быть настолько длинным, насколько это необходимо:
```python
>>> print(123123123123123123123123123123123123123123123123 + 1)
123123123123123123123123123123123123123123123124
```
Python интерпретирует последовательность десятичных цифр без префикса как десятичное число:
```python
>>> print(10)
10
```
Следующие строки могут быть добавлены к целочисленному значению, чтобы указать основание, отличное от 10:

| Префикс | интерпретация | Основыание |
| --- | --- | --- |
| 0b (ноль + 'b' в нижнем регистре); 0B (ноль + 'B' в верхнем регистре) | двоичный | 2 |
| 0o (ноль + 'o' в нижнем регистре); 0O (ноль + 'O' в верхнем регистре) | восьмеричный | 8 |
| 0x (ноль + 'x' в нижнем регистре); 0X (ноль + 'X' в верхнем регистре) | шестнадцатеричный | 16 |

```python
>>> print(0o10)
8

>>> print(0x10)
16

>>> print(0b10)
2
```
Базовый тип целого числа Python, независимо от базы, используемой для его указания, называется int:
```python
>>> type(10)
<class 'int'>
>>> type(0o10)
<class 'int'>
>>> type(0x10)
<class 'int'>
```
### Числа с плавающей точкой (Floating-Point Numbers)
Тип с плавающей точкой в Python обозначает число с плавающей точкой.
значения с плавающей точкой (float) указываются с десятичной точкой.
По желанию, символ e или E, за которым следует положительное или отрицательное целое число, может быть добавлен для указания научной записи [Экспоненциальная запись](https://ru.wikipedia.org/wiki/%D0%AD%D0%BA%D1%81%D0%BF%D0%BE%D0%BD%D0%B5%D0%BD%D1%86%D0%B8%D0%B0%D0%BB%D1%8C%D0%BD%D0%B0%D1%8F_%D0%B7%D0%B0%D0%BF%D0%B8%D1%81%D1%8C):
```python
>>> 4.2
4.2
>>> type(4.2)
<class 'float'>
>>> 4.
4.0
>>> .2
0.2

>>> .4e7
4000000.0
>>> type(.4e7)
<class 'float'>
>>> 4.2e-4
0.00042
```

285/5000
Почти все платформы представляют значения с плавающей точкой Python как 64-битные значения «двойной точности», в соответствии со стандартом IEEE 754. В этом случае максимальное значение, которое может иметь число с плавающей запятой, составляет приблизительно 1,8 ⨉ 10308. Python будет указывать число, большее, чем это значение в строке inf(бесконечность):
```python
>>> 1.79e308
1.79e+308
>>> 1.8e308
inf
```
Ближайшее ненулевое число может быть равно нулю примерно 5,0 ⨉ 10-324. 
Все, что ближе к нулю, чем это, фактически равно нулю:
```python
>>> 5e-324
5e-324
>>> 1e-325
0.0
```
### Комплексные числа (Complex Numbers)
Комплексные числа определены как <действительная часть> + <мнимая часть> j. Например:
```python
>>> 2+3j
(2+3j)
>>> type(2+3j)
<class 'complex'>
```
### Строки (Strings)
Строки - это последовательности символьных данных. Тип строки в Python называется str.
Строковые литералы могут быть разделены одинарными или двойными кавычками.
Все символы между открывающим разделителем и соответствующим закрывающим разделителем являются частью строки:
```python
>>> print("I am a string.")
I am a string.
>>> type("I am a string.")
<class 'str'>

>>> print('I am too.')
I am too.
>>> type('I am too.')
<class 'str'>
```
Строка в Python может содержать столько символов, сколько вы хотите. Единственным ограничением являются ресурсы памяти вашей машины. Строка также может быть пустой:
```python
>>> ''
''
```
Если вы хотите включить любой тип символа кавычки в строку, самый простой способ - разделить строку с другим типом. Если строка должна содержать одинарную кавычку, разделите ее двойными кавычками и наоборот:
```python
>>> print("This string contains a single quote (') character.")
This string contains a single quote (') character.

>>> print('This string contains a double quote (") character.')
This string contains a double quote (") character.
```
или используйет слеш
```python
>>> print('This string contains a single quote (\') character.')
This string contains a single quote (') character.
```
Ниже приведена таблица escape-последовательностей, которые заставляют Python подавлять обычную специальную интерпретацию символа в строке:

| Escape последовательность | Обычная интерпретация сиволов после обратной косой черты | "Escaped" итерпритация |
| --- | --- | --- |
| \' | Завершает строку символом открытия одинарной кавычки | Одинарная кавычка (') | 
| \" | Завершает строку двойным кавычком | двойная кавычка (") |
| \newline | Завершает строку ввода | Новая строка игнорируется |
| \\ | Вводит escape-последовательность | Cимвол обратной косой черты (\)|

Обычно символ новой строки завершает ввод строки. Поэтому нажатие Enter в середине строки заставит Python думать, что она неполная:
```python
>>> print('a

SyntaxError: EOL while scanning string literal
```
Чтобы разбить строку на более чем одну строку, добавляйте обратную косую черту перед каждой новой строкой, и новые строки будут игнорироваться:
```python
>>> print('a\
... b\
... c')
abc
```
Чтобы включить буквенную обратную косую черту в строку, экранируйте ее обратной косой чертой:
```python
>>> print('foo\\bar')
foo\bar
```
### Сырые строки (Raw Strings)
Необработанному строковому литералу предшествует r или R, что указывает на то, что escape-последовательности в связанной строке не транслируются. Символ обратной косой черты остается в строке:
```python
>>> print('foo\nbar')
foo
bar
>>> print(r'foo\nbar')
foo\nbar

>>> print('foo\\bar')
foo\bar
>>> print(R'foo\\bar')
foo\\bar
```
### Строки в тройных кавычках (Triple-Quoted Strings)
Существует еще один способ разграничения строк в Python. Строки с тройными кавычками ограничиваются соответствующими группами из трех одинарных или трех двойных кавычек. Последовательности Escape по-прежнему работают в строках с тройными кавычками, но одиночные кавычки, двойные кавычки и символы новой строки могут быть включены без их выхода. Это обеспечивает удобный способ создания строки с одинарными и двойными кавычками:

```python
>>> print('''This string has a single (') and a double (") quote.''')
This string has a single (') and a double (") quote.
```

Поскольку переводы строк могут быть включены без их выхода, это также позволяет использовать многострочные строки:

```python
>>> print("""This is a
string that spans
across several lines""")
This is a
string that spans
across several lines
```
### Логический тип (Boolean Type, Boolean Context, and “Truthiness”)

Python 3 предоставляет логический тип данных. Объекты типа Boolean могут иметь одно из двух значений: True или False:
```python
>>> type(True)
<class 'bool'>
>>> type(False)
<class 'bool'>
```

Выражения в Python часто оцениваются в логическом контексте, что означает, что они интерпретируются для представления правды или лжи. Значение, которое является истинным в булевом контексте, иногда называют «правдивым», а значение, которое является ложным в булевом контексте, называют «ложным» (вы также можете увидеть «ложное», записанное как «ложный»).

«Истинность» объекта булева типа очевидна: булевы объекты, равные Истине, являются правдивыми (true), а объекты, равные Ложным, являются ложными (false). Но не-булевы объекты могут быть оценены также в булевом контексте и определены как истинные или ложные.

### Встроенные функции
Интерпретатор Python поддерживает множество встроенных функций: шестьдесят восемь, начиная с Python 3.6. Вы расскажете о многих из них в следующих обсуждениях, так как они встречаются в контексте

Полный спискл [тут](https://docs.python.org/3.6/library/functions.html)

Обратите внимание на:
- chr() возвращает строковое представление символа, заданного целочисленным аргументом;
- str() возвращает строковую версию объекта;
- type() возвращает тип объекта или создает новый тип объекта;

- all() возвращает True, если все элементы итерируемого являются истинными;
- any() dозвращает True, если какие-либо элементы итерируемого верны;
- filter() фильтрует элементы из итерируемого;
- len() возвращает длину объекта;
- range() создает диапазон целочисленных значений;
- slice() возвращает slice объект;
- sorted() возвращает отсортированный список из повторяемого;
