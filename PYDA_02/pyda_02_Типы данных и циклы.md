
# Лекция 02. Типы данных и циклы

## Оглавление:
* [02.01. Простые типы данных](#1)
* [02.02. Строки](#2)
* [02.03. Списки](#3)
    * [02.03.01. Распаковка списков](#4)
    * [02.03.02. Операции со списками](#5)
* [02.04. Списки и строки](#6)
* [02.05. Tuple (кортежы)](#7)
* [02.06. Множества (set)](#8)
* [02.07. Словари](#9)
* [02.08. Циклы](#10)




## 02.01. Простые типы данных <a class="anchor" id="1"></a>

* integer (целые числа);
* float (числа с плавающей точкой);
* string (строка/текст);
* boolean (булевый/логический тип).

***type()*** - Узнать тип объекта

***int(),float(), bool(), str()*** - Изменить тип объекта


```python
my_integer = 10
type(my_integer)
```




    int




```python
my_float = 5.5
type(my_float)
```




    float




```python
my_string = 'Hello World!'
my_string_2 = "Hello World"
type(my_string)
```




    str




```python
my_bool = True
my_bool = False
type(my_bool)
```




    bool




```python
x = 5
y = 1
print(type(x > y))
```

    <class 'bool'>
    

### 02.01.01.  Преобразование типа объекта

***int(),float(), bool(), str()*** - Изменить тип объекта


```python
# Не работает
salary = 1000
print('Ваша годовая зарплата составляет ' + salary + ' условных единиц')
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-8-6e7762799e71> in <module>()
          1 # Не работает
          2 salary = 1000
    ----> 3 print('Ваша годовая зарплата составляет ' + salary + ' условных единиц')
    

    TypeError: must be str, not int



```python
# Работает
print('Ваша годовая зарплата составляет ' + str(salary) + ' условных единиц')
```

    Ваша годовая зарплата составляет 1000 условных единиц
    


```python
# неявное преобразование типов
print(1 + True)
print(20 / 5.1)
```

    2
    3.9215686274509807
    

## 02.02. Строки <a class="anchor" id="2"></a>

**Операции со строками**:
1. **+** - Конкатенация стррок
2. Умножение строки на число = повторение строки
3. **.upper()**  - приводит строку к верхнему регистру;
4. **.lower()**  - приводит строку к нижнему регистру;
5. **.capitalize()** приводит первую букву к верхнему регистру;
6. **.replace('что заменить', 'на что заменить')** заменяет элемент в строке на указанный;
7. **len(my_string)** позволяет определить длину строки (количество символов в ней);
8. Другие


```python
'Конка'+'тенация'
```




    'Конкатенация'




```python
my_string * 3
```




    'Hello World!Hello World!Hello World!'




```python
my_string.upper()
```




    'HELLO WORLD!'




```python
my_string.lower()
```




    'hello world!'




```python
my_string.capitalize() # Первую букву каждого слова к верхнему регистру
```




    'Hello world!'




```python
my_string.replace('Hello', 'Goodbye')
```




    'Goodbye World!'




```python
len(my_string)
```




    12




```python
# индексация и срезы
my_string = 'Hello World'
```


```python
my_string[2]
```




    'l'




```python
my_string[-4]
```




    'o'




```python
my_string[0:5] # Первый элемент включительно, последний нет
```




    'Hello'




```python
my_string[0:8:2] # С шагом 2
```




    'HloW'




```python
my_string[6:]
```




    'World'




```python
my_string[:5]
```




    'Hello'




```python
my_string[::-1]
```




    'dlroW olleH'




```python
# проверка на вхождение элемента в объект при помощи in (есть обратная операция not in)
target_string = 'Wo'
if target_string in my_string:
    print('find!')
```

    find!
    

### f-строки

Добавляя префикс f к строке можно встраивать в нее
произвольные выражения при помощи фигурных
скобок – {}.


```python
# f-строки
name = 'oleg'
f"Hello, {name.capitalize()}"
```




    'Hello, Oleg'



## 02.03. Списки <a class="anchor" id="3"></a>
Хранение объектов различных типов. Изменяемый тип данных.


```python
month_list = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep']
income_list = [13000, 14000, 14300, 15000, 13800, 13000, 14900, 15200, 15300]
income_by_months = [['Jan', 13000], ['Feb', 14000], ['Mar', 14300], ['Apr', 15000], ['May', 13800], ['Jun', 13000], ['Jul', 14900], ['Aug', 15200], ['Sep', 15300]]
```


```python
print(type(month_list))
print(type(income_list))
print(type(income_by_months))
```

    <class 'list'>
    <class 'list'>
    <class 'list'>
    


```python
# индексация элементов в списке
print(month_list[0])
print(month_list[-1])
print(income_by_months[-4])
```

    Jan
    Sep
    ['Jun', 13000]
    


```python
# срезы
print(income_by_months[0:2])
print('--------------')
print(income_by_months[-8:-6])
print('--------------')
print(income_by_months[2:])
print('--------------')
print(income_by_months[:3])
```

    [['Jan', 13000], ['Feb', 14000]]
    --------------
    [['Feb', 14000], ['Mar', 14300]]
    --------------
    [['Mar', 14300], ['Apr', 15000], ['May', 13800], ['Jun', 13000], ['Jul', 14900], ['Aug', 15200], ['Sep', 15300]]
    --------------
    [['Jan', 13000], ['Feb', 14000], ['Mar', 14300]]
    


```python
# можно обращаться к любому уровню вложенности
income_by_months[0][0] # из списка выбираем первый элемент, а в нем еще один 1-ый из двух
```




    'Jan'




```python
# изменение списков
income_by_months[0][1] = 13100
print(income_by_months)
```

    [['Jan', 13100], ['Feb', 14000], ['Mar', 14300], ['Apr', 15000], ['May', 13800], ['Jun', 13000], ['Jul', 14900], ['Aug', 15200], ['Sep', 15300]]
    


```python
income_by_months[0:2] = [['Jan', 13200], ['Feb', 13900]]
print(income_by_months)
```

    [['Jan', 13200], ['Feb', 13900], ['Mar', 14300], ['Apr', 15000], ['May', 13800], ['Jun', 13000], ['Jul', 14900], ['Aug', 15200], ['Sep', 15300]]
    


```python
income_by_months_2 = [['Nov', 15400], ['Dec', 17000]]
income_by_month = income_by_months + income_by_months_2
print(income_by_month)
```

    [['Jan', 13200], ['Feb', 13900], ['Mar', 14300], ['Apr', 15000], ['May', 13800], ['Jun', 13000], ['Jul', 14900], ['Aug', 15200], ['Sep', 15300], ['Nov', 15400], ['Dec', 17000]]
    


```python
# сумма элементов
sum(income_list)
```




    128500




```python
# сортировка по возрастанию
sorted(income_list)
```




    [13000, 13000, 13800, 14000, 14300, 14900, 15000, 15200, 15300]




```python
# изменить порядок сортировки
sorted(income_list, reverse = True)
```




    [15300, 15200, 15000, 14900, 14300, 14000, 13800, 13000, 13000]




```python
# а это сортировка строк по алфавиту
sorted(month_list)
```




    ['Apr', 'Aug', 'Feb', 'Jan', 'Jul', 'Jun', 'Mar', 'May', 'Sep']



## 02.03.01. Распаковка списков <a class="anchor" id="4"></a>


```python
first, second, third = ['первый', 'второй', 'третий']
second 
```




    'второй'




```python
# когда число элементов неизвестно
first, *other = ['первый', 'второй', 'третий']
first, other
```




    ('первый', ['второй', 'третий'])




```python
first, *_, last =  ['первый', 'второй', 'третий', 'четвертый']
```


```python
first, last
```




    ('первый', 'четвертый')



## 02.03.02. Операции со списками <a class="anchor" id="5"></a>


```python
# Допустим у нас есть список
income_by_months
```




    [['Jan', 13200],
     ['Feb', 13900],
     ['Mar', 14300],
     ['Apr', 15000],
     ['May', 13800],
     ['Jun', 13000],
     ['Jul', 14900],
     ['Aug', 15200],
     ['Sep', 15300]]




```python
# Удаляем элемент по индексу
del(income_by_months[-1])
income_by_months
```




    [['Jan', 13200],
     ['Feb', 13900],
     ['Mar', 14300],
     ['Apr', 15000],
     ['May', 13800],
     ['Jun', 13000],
     ['Jul', 14900],
     ['Aug', 15200]]




```python
month_list
```




    ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep']




```python
# удаляем элемент по значению
month_list.remove('Jan')
print(month_list)
```

    ['Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep']
    


```python
# добавляем элемент в конец списка
income_by_months.append(['Dec', 17000])
income_by_months
```




    [['Jan', 13200],
     ['Feb', 13900],
     ['Mar', 14300],
     ['Apr', 15000],
     ['May', 13800],
     ['Jun', 13000],
     ['Jul', 14900],
     ['Aug', 15200],
     ['Dec', 17000]]




```python
# добавляем элемент по нужному индексу
income_list.insert(2, 1111111)
print(income_list)
```

    [13000, 14000, 1111111, 14300, 15000, 13800, 13000, 14900, 15200, 15300]
    


```python
# считаем количество вхождений элемента в список
income_list.count(13000)
```




    2




```python
# узнаем индекс элемента в списка (только первое вхождение!)
income_list.index(13000)
```




    0




```python
# разворачиваем список
month_list.reverse()
month_list
```




    ['Sep', 'Aug', 'Jul', 'Jun', 'May', 'Apr', 'Mar', 'Feb']




```python
# узнаем длину списка
len(income_list)
```




    10



## 02.06. Списки и строки <a class="anchor" id="6"></a>


```python
queries_string = "смотреть сериалы онлайн,новости спорта,афиша кино,курс доллара,сериалы этим летом,курс по питону,сериалы про спорт"
```


```python
# преобразование строки в список (например, из CSV-файла)
queries_string.split(',')
```




    ['смотреть сериалы онлайн',
     'новости спорта',
     'афиша кино',
     'курс доллара',
     'сериалы этим летом',
     'курс по питону',
     'сериалы про спорт']




```python
# Преобразование списка в строку

','.join(['Столбец 1', 'Столбец 2', 'Столбец 3'])
```




    'Столбец 1,Столбец 2,Столбец 3'




```python
# проверка вхождения элемента в список:

#'Москва' in ['Ленинград', 'Одесса', 'Севастополь', 'Москва']
'Москва' not in ['Ленинград', 'Одесса', 'Севастополь', 'Москва']
```




    False



## 02.05. Tuple (кортежы) <a class="anchor" id="7"></a>

**Кортежи (tuples)** – неизменяемые списки (нельзя добавлять или удалять элементы из уже созданного кортежа).
* Инициализируется при помощи **()**.
* Занимает меньше памяти при работе с ними по сравнению со списками.


```python
# Создаем кортеж
salary_tuple = (1000, 1200, 1300, 900, 800)
type(salary_tuple)
```




    tuple




```python
print(salary_tuple[0]) # Выбираем первый элемент кортежа
salary_tuple[0] = 500  # Присваиваем первому элементу кортежа новое значение. Не работает - кортеж изменять нельзя
```

    1000
    


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-36-958f8f97b050> in <module>()
          1 print(salary_tuple[0]) # Выбираем первый элемент кортежа
    ----> 2 salary_tuple[0] = 500  # Присваиваем первому элементу кортежа новое значение. Не работает - кортеж изменять нельзя
    

    TypeError: 'tuple' object does not support item assignment



```python
# кортеж из одного элемента задается так:
t = ('one', )
```


```python
# без запятой получится строка
type( ('one') )
```




    str



### Функция ZIP
Над кортежами доступны все операции над списками, не изменяющие список.

**Функция zip(list_1, list_2, ...)** берёт на вход несколько списков и создаёт из них специальный zip-объект, состоящий из кортежей, такой, что первый элемент полученного объекта содержит кортеж из первых элементов всех списков-аргументов.


```python
# Задаем 2 списка
salaries = [1000, 1200, 1300, 900, 800, 1000]
names = ['Robert', 'Jane', 'Liza', 'Richard', 'John']
# Создаем zip-объект
salaries_by_names = zip(names, salaries)
# print(salaries_by_names)
print(list(salaries_by_names))
# Так же работает и для большего кол-ва элементов
```

    [('Robert', 1000), ('Jane', 1200), ('Liza', 1300), ('Richard', 900), ('John', 800)]
    


```python
list = [[0,1][][][]]
```


      File "<ipython-input-47-998510712b29>", line 1
        list = [[0,1][][][]]
                      ^
    SyntaxError: invalid syntax
    


## 02.06. Множества (set) <a class="anchor" id="8"></a>
Набор ("контейнер") неповторяющихся элементов в случайном порядке

Инициализируется при помощи **set()**, как правило создаются из списков.


```python
# Создаем множества
data_scientist_skills = set(['Python', 'R', 'SQL', 'Tableau', 'SAS', 'Git'])
data_engineer_skills = set(['Python', 'Java', 'Scala', 'Git', 'SQL', 'Hadoop'])
```


```python
# логическое ИЛИ – что нужно знать data-scientst, который по совместительству data-engineer
print(data_scientist_skills.union(data_engineer_skills))
print(data_scientist_skills | data_engineer_skills) # Более простой способ записи
```

    {'R', 'SAS', 'SQL', 'Python', 'Java', 'Scala', 'Hadoop', 'Git', 'Tableau'}
    {'R', 'SAS', 'SQL', 'Python', 'Java', 'Scala', 'Hadoop', 'Git', 'Tableau'}
    


```python
# логическое И – что нужно знать и data-scientst и data-engineer
print(data_scientist_skills.intersection(data_engineer_skills))
print(data_scientist_skills & data_engineer_skills)
```

    {'SQL', 'Git', 'Python'}
    {'SQL', 'Git', 'Python'}
    


```python
# разность множеств – что знает data-scientist, но не знает data-engineer (и наоборот)
print(data_scientist_skills.difference(data_engineer_skills))
print(data_scientist_skills - data_engineer_skills)
# разность множеств – что знает data-engineer, но не знает data-scientist
print(data_engineer_skills.difference(data_scientist_skills))
print(data_engineer_skills - data_scientist_skills)
```

    {'R', 'SAS', 'Tableau'}
    {'R', 'SAS', 'Tableau'}
    {'Hadoop', 'Scala', 'Java'}
    {'Hadoop', 'Scala', 'Java'}
    


```python
# симметричная разность множеств – что такого знают data-scientist и data-engineer
print(data_scientist_skills.symmetric_difference(data_engineer_skills))
print(data_scientist_skills ^ data_engineer_skills)
# чего не знают они оба вместе
print(data_engineer_skills.symmetric_difference(data_scientist_skills))
print(data_engineer_skills ^ data_scientist_skills)
```

    {'R', 'Hadoop', 'SAS', 'Tableau', 'Java', 'Scala'}
    {'R', 'Hadoop', 'SAS', 'Tableau', 'Java', 'Scala'}
    {'R', 'SAS', 'Java', 'Hadoop', 'Scala', 'Tableau'}
    {'R', 'SAS', 'Java', 'Hadoop', 'Scala', 'Tableau'}
    

## 02.07. Словари <a class="anchor" id="9"></a>

* Неупорядоченные (в последних версиях могут быть упорядоченными) коллекции произвольных объектов с доступом по ключу.
* Инициализируется при помощи **{ }**, элементы них хранятся в формате **key:value**.
* Ключами могут быть **strings**, **booleans**, **integers** и **floats**.
* Любое значение из словаря можно получить следующим образом: **my_dict[key]**.
* Все ключи в словаре должны быть уникальными.


```python
# Создание словаря
staff_salary = {'Robert': 800, 
                'Jane': 2000, 
                'Liza': 1300, 
                'Richard': 800, 
                'Tom': 1100, 
                'Bob': 1300}
```


```python
# обращение к элементу словаря
staff_salary['Jane']
```




    2000




```python
# добавляем элемент в словарь
staff_salary['Rayan'] = 2000
staff_salary
```




    {'Bob': 1300,
     'Jane': 2000,
     'Liza': 1300,
     'Rayan': 2000,
     'Richard': 800,
     'Robert': 800,
     'Tom': 1100}




```python
staff_dict = {
    'Robert': {'salary': 800, 'bonus': 200}, 
    'Jane': {'salary': 200, 'bonus': 300}, 
    'Liza': {'salary': 1300, 'bonus': 200}, 
    'Richard': {'salary': 500, 'bonus': 1200}
}
```


```python
staff_dict['Robert']['bonus']
```




    200




```python
# удаляем элемент из словаря
del(staff_salary['Liza'])
staff_salary
```




    {'Bob': 1300,
     'Jane': 2000,
     'Rayan': 2000,
     'Richard': 800,
     'Robert': 800,
     'Tom': 1100}




```python
# Выбираем несуществующий элемент
staff_dict['Oleg']
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-66-b52f44c6b4a1> in <module>()
          1 # Выбираем несуществующий элемент
    ----> 2 staff_dict['Oleg']
    

    KeyError: 'Oleg'



```python
# безопасно получаем значение по ключу
staff_dict.get('Oleg', 'Not Found')
#staff_dict.get('Robert', 'Not Found')
```




    'Not Found'




```python
# получаем только ключи/значения из словаря (очень пригодиться в циклах)
print(staff_salary.keys()) # Все ключи
print(staff_salary.values())# Все все значения
print(staff_salary.items()) # Все пары (элементы словаря, в данном случае тоже словари)
```

    dict_keys(['Robert', 'Jane', 'Richard', 'Tom', 'Bob', 'Rayan'])
    dict_values([800, 2000, 800, 1100, 1300, 2000])
    dict_items([('Robert', 800), ('Jane', 2000), ('Richard', 800), ('Tom', 1100), ('Bob', 1300), ('Rayan', 2000)])
    

## 02.08. Циклы <a class="anchor" id="10"></a>

### Цикл While

![image.png](attachment:image.png)


```python
x = 5
while x != 0:
    print(x)
    x = x - 1
#     x -= 1 - другая запись x = x - 1
```

    5
    4
    3
    2
    1
    


```python
x = 7
while x != 0:
    if x % 2 == 0:
        print(x, '- четное число')
        x = x - 1
    else:
        print(x, '- нечетное число')
        x = x - 1
```

    7 - нечетное число
    6 - четное число
    5 - нечетное число
    4 - четное число
    3 - нечетное число
    2 - четное число
    1 - нечетное число
    

### Цикл For
Цикл **for** проходится по элементам любого итерируемого объекта (строки, списка и т.д.) и во время каждого прохода выполняет
заданную последовательность действий.

![image.png](attachment:image.png)


```python
# итерация по строкам
company_name = 'Orange'
for letter in company_name:
    letter = letter.capitalize()
    print(letter)
```

    O
    R
    A
    N
    G
    E
    


```python
# итерация по спискам
companies_capitalization = [
 ['Orange', 1.3],
 ['Maxisoft', 1.5],
 ['Headbook', 0.8],
 ['Nicola', 2.2]
]
for company in companies_capitalization:
    print(company[0], 'capitalization is', company[1])
```

    Orange capitalization is 1.3
    Maxisoft capitalization is 1.5
    Headbook capitalization is 0.8
    Nicola capitalization is 2.2
    


```python
# список списков списков. Список, который состоит из списков в котором есть списки 
countries_temperature = [
 ['Thailand', [75.2, 77, 78.8, 73.4, 68, 75.2, 77]],
 ['Germany', [57.2, 55.4, 59, 59, 53.6, 55.4, 57.2]],
 ['Russia', [35.6, 37.4, 39.2, 41, 42.8, 39.2, 35.6]],
 ['Poland', [50, 50, 53.6, 57.2, 55.4, 55.4, 51.8]],
]
```


```python
for country in countries_temperature:
#     print (country)
    cel_temp = (sum(country[1]) / len(country[1])-32) * 5 / 9
    print (f'{country[0]} - {round(cel_temp, 2)}')
#     print(f'{country[0]} - {round(cel_temp, 2)}')
```

    Thailand - 23.86
    Germany - 13.71
    Russia - 3.71
    Poland - 11.86
    


```python
# Более сложный вариант
for country in countries_temperature:
    average_temp = 0
    for temperature in country[1]:
        average_temp += (temperature - 32) * 5 / 9
    print(round(average_temp/len(country[1]), 2))
```

    23.86
    13.71
    3.71
    11.86
    


```python
# итерация по словарям
# так бы было без цикла
salaries = {
    'John': 1200,
    'Mary': 500,
    'Steven': 1000,
    'Liza': 1500
}
print("John's salary:", salaries['John'])
print("Mary's salary:", salaries['John'])
print("Steven's salary:", salaries['John'])
print("Liza's salary:", salaries['John'])
```

    John's salary: 1200
    Mary's salary: 1200
    Steven's salary: 1200
    Liza's salary: 1200
    


```python
# используем цикл
for person, salary in salaries.items():
    print(person, "'s salary: ", salary, sep='')
```

    John's salary: 1200
    Mary's salary: 500
    Steven's salary: 1000
    Liza's salary: 1500
    


```python
# добавим уровень з/п
for person in salaries:
    status = ''
    if salaries[person] > 1000:
        status = 'above average'
    else:
        status = 'below average'
    print(person, "'s salary: ", salaries[person], ' (', status, ')', sep='')
```

    John's salary: 1200 (above average)
    Mary's salary: 500 (below average)
    Steven's salary: 1000 (below average)
    Liza's salary: 1500 (above average)
    


```python
# добавим нумерацию (функция enumerate выдает и строку и индекс)
for index, person in enumerate(salaries): 
    status = ''
    if salaries[person] > 1000:
        status = 'above average'
    else:
        status = 'below average'
    print(index + 1, '. ', person, "'s salary: ", salaries[person], ' (', status, ')', sep='')
```

    1. John's salary: 1200 (above average)
    2. Mary's salary: 500 (below average)
    3. Steven's salary: 1000 (below average)
    4. Liza's salary: 1500 (above average)
    

## Функции break, pass, continue


```python
phrase = '640Кб должно хватить для любых задач. Билл Гейтс (по легенде)'
```


```python
# break - прерывает цикл
for letter in phrase:
    if letter == ' ':
        break
    print(letter)
print('finish loop')
```

    6
    4
    0
    К
    б
    finish loop
    


```python
# continue - пропускает шаг цикла
for letter in phrase:
    if letter == ' ':
        continue
    print(letter)
print('finish loop')
```

    6
    4
    0
    К
    б
    д
    о
    л
    ж
    н
    о
    х
    в
    а
    т
    и
    т
    ь
    д
    л
    я
    л
    ю
    б
    ы
    х
    з
    а
    д
    а
    ч
    .
    Б
    и
    л
    л
    Г
    е
    й
    т
    с
    (
    п
    о
    л
    е
    г
    е
    н
    д
    е
    )
    finish loop
    


```python
# pass - ничего не делает. Используется, как заглушка
for letter in phrase:
    if letter == ' ':
        pass
    print(letter)
print('finish loop')
```

    6
    4
    0
    К
    б
     
    д
    о
    л
    ж
    н
    о
     
    х
    в
    а
    т
    и
    т
    ь
     
    д
    л
    я
     
    л
    ю
    б
    ы
    х
     
    з
    а
    д
    а
    ч
    .
     
    Б
    и
    л
    л
     
    Г
    е
    й
    т
    с
     
    (
    п
    о
     
    л
    е
    г
    е
    н
    д
    е
    )
    finish loop
    

### Функция range


```python
range(10) # генерирует последовательность чисел
```




    range(0, 10)




```python
list(range(10))
```




    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]




```python
for i in range(10):
    print(i)
```

    0
    1
    2
    3
    4
    5
    6
    7
    8
    9
    


```python
# с указанием левой и правой границы
for i in range(3, 20):
    print(i)
```

    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    17
    18
    19
    


```python
# третий аргумент - шаг
for i in range(3, 20, 5):
    print(i)
```

    3
    8
    13
    18
    

### Практика


```python
# Есть блюдо и словарь и списки игридиентов
# Задача: Сделать список покупок. Задаются какие блюда и на сколько человек готовится
cook_book = {
  'салат': [
     {'ingridient_name': 'сыр', 'quantity': 50, 'measure': 'гр'},
     {'ingridient_name': 'томаты', 'quantity': 20, 'measure': 'гр'},
     {'ingridient_name': 'огурцы', 'quantity': 20, 'measure': 'гр'},
     {'ingridient_name': 'маслины', 'quantity': 10, 'measure': 'гр'},
     {'ingridient_name': 'оливковое масло', 'quantity': 20, 'measure': 'мл'},
     {'ingridient_name': 'салат', 'quantity': 10, 'measure': 'гр'},
     {'ingridient_name': 'перец', 'quantity': 20, 'measure': 'гр'}
    ],
  'пицца': [
     {'ingridient_name': 'сыр', 'quantity': 20, 'measure': 'гр'},
     {'ingridient_name': 'колбаса', 'quantity': 30, 'measure': 'гр'},
     {'ingridient_name': 'бекон', 'quantity': 30, 'measure': 'гр'},
     {'ingridient_name': 'оливки', 'quantity': 10, 'measure': 'гр'},
     {'ingridient_name': 'томаты', 'quantity': 20, 'measure': 'гр'},
     {'ingridient_name': 'тесто', 'quantity': 100, 'measure': 'гр'},   
    ],
  'лимонад': [
     {'ingridient_name': 'лимон', 'quantity': 1, 'measure': 'шт'},
     {'ingridient_name': 'вода', 'quantity': 200, 'measure': 'мл'},
     {'ingridient_name': 'сахар', 'quantity': 10, 'measure': 'гр'},
     {'ingridient_name': 'лайм', 'quantity': 20, 'measure': 'гр'},    
    ]
}
```


```python
person_count = 3 # на скольких людей готовить
shop_list = {} # создаем словарь список покупок

for dish in cook_book:
    #print(dish)
    for ingridient in cook_book[dish]:
        #print(ingridient)
        new_shop_list_item = dict(ingridient)
        new_shop_list_item['quantity'] = ingridient['quantity'] * person_count
#        shop_list[new_shop_list_item['ingridient_name']] = new_shop_list_item
#print(shop_list)  
        # если название элемента нет в словаре, записываем, иначе складываем: 
        # обращаемся к словарю по элементу кол-во и добавляем значение по ключу количества
        if new_shop_list_item['ingridient_name'] not in shop_list:
            shop_list[new_shop_list_item['ingridient_name']] = new_shop_list_item 
        else:
            shop_list[new_shop_list_item['ingridient_name']]['quantity'] += new_shop_list_item['quantity']  
            
shop_list            
```




    {'бекон': {'ingridient_name': 'бекон', 'measure': 'гр', 'quantity': 90},
     'вода': {'ingridient_name': 'вода', 'measure': 'мл', 'quantity': 600},
     'колбаса': {'ingridient_name': 'колбаса', 'measure': 'гр', 'quantity': 90},
     'лайм': {'ingridient_name': 'лайм', 'measure': 'гр', 'quantity': 60},
     'лимон': {'ingridient_name': 'лимон', 'measure': 'шт', 'quantity': 3},
     'маслины': {'ingridient_name': 'маслины', 'measure': 'гр', 'quantity': 30},
     'огурцы': {'ingridient_name': 'огурцы', 'measure': 'гр', 'quantity': 60},
     'оливки': {'ingridient_name': 'оливки', 'measure': 'гр', 'quantity': 30},
     'оливковое масло': {'ingridient_name': 'оливковое масло',
      'measure': 'мл',
      'quantity': 60},
     'перец': {'ingridient_name': 'перец', 'measure': 'гр', 'quantity': 60},
     'салат': {'ingridient_name': 'салат', 'measure': 'гр', 'quantity': 30},
     'сахар': {'ingridient_name': 'сахар', 'measure': 'гр', 'quantity': 30},
     'сыр': {'ingridient_name': 'сыр', 'measure': 'гр', 'quantity': 210},
     'тесто': {'ingridient_name': 'тесто', 'measure': 'гр', 'quantity': 300},
     'томаты': {'ingridient_name': 'томаты', 'measure': 'гр', 'quantity': 120}}




```python
for shop_list_item in shop_list.values():
    print(f'{shop_list_item["ingridient_name"]}, {shop_list_item["quantity"]}{shop_list_item["measure"]}')
```

    сыр, 210гр
    томаты, 120гр
    огурцы, 60гр
    маслины, 30гр
    оливковое масло, 60мл
    салат, 30гр
    перец, 60гр
    колбаса, 90гр
    бекон, 90гр
    оливки, 30гр
    тесто, 300гр
    лимон, 3шт
    вода, 600мл
    сахар, 30гр
    лайм, 60гр
    


```python
person_count = 3
shop_list = {}
for dish in cook_book:
    for ingridient in cook_book[dish]:
        new_shop_list_item = dict(ingridient)
        new_shop_list_item['quantity'] = ingridient['quantity'] * person_count
        if new_shop_list_item['ingridient_name'] not in shop_list:
            shop_list[new_shop_list_item['ingridient_name']] = new_shop_list_item
        else:
            shop_list[new_shop_list_item['ingridient_name']]['quantity'] += new_shop_list_item['quantity']
shop_list
```




    {'бекон': {'ingridient_name': 'бекон', 'measure': 'гр', 'quantity': 90},
     'вода': {'ingridient_name': 'вода', 'measure': 'мл', 'quantity': 600},
     'колбаса': {'ingridient_name': 'колбаса', 'measure': 'гр', 'quantity': 90},
     'лайм': {'ingridient_name': 'лайм', 'measure': 'гр', 'quantity': 60},
     'лимон': {'ingridient_name': 'лимон', 'measure': 'шт', 'quantity': 3},
     'маслины': {'ingridient_name': 'маслины', 'measure': 'гр', 'quantity': 30},
     'огурцы': {'ingridient_name': 'огурцы', 'measure': 'гр', 'quantity': 60},
     'оливки': {'ingridient_name': 'оливки', 'measure': 'гр', 'quantity': 30},
     'оливковое масло': {'ingridient_name': 'оливковое масло',
      'measure': 'мл',
      'quantity': 60},
     'перец': {'ingridient_name': 'перец', 'measure': 'гр', 'quantity': 60},
     'салат': {'ingridient_name': 'салат', 'measure': 'гр', 'quantity': 30},
     'сахар': {'ingridient_name': 'сахар', 'measure': 'гр', 'quantity': 30},
     'сыр': {'ingridient_name': 'сыр', 'measure': 'гр', 'quantity': 210},
     'тесто': {'ingridient_name': 'тесто', 'measure': 'гр', 'quantity': 300},
     'томаты': {'ingridient_name': 'томаты', 'measure': 'гр', 'quantity': 120}}




```python
for shop_list_item in shop_list.values():
    print(f'{shop_list_item["ingridient_name"]}, {shop_list_item["quantity"]}{shop_list_item["measure"]}')
```

    сыр, 210гр
    томаты, 120гр
    огурцы, 60гр
    маслины, 30гр
    оливковое масло, 60мл
    салат, 30гр
    перец, 60гр
    колбаса, 90гр
    бекон, 90гр
    оливки, 30гр
    тесто, 300гр
    лимон, 3шт
    вода, 600мл
    сахар, 30гр
    лайм, 60гр
    

### Домашнее задание

## Задание 1

Дан список с визитами по городам и странам. 
Напишите код, который возвращает отфильтрованный список geo_logs, содержащий только визиты из России.


```python
geo_logs = [
    {'visit1': ['Москва', 'Россия']},
    {'visit2': ['Дели', 'Индия']},
    {'visit3': ['Владимир', 'Россия']},
    {'visit4': ['Лиссабон', 'Португалия']},
    {'visit5': ['Париж', 'Франция']},
    {'visit6': ['Лиссабон', 'Португалия']},
    {'visit7': ['Тула', 'Россия']},
    {'visit8': ['Тула', 'Россия']},
    {'visit9': ['Курск', 'Россия']},
    {'visit10': ['Архангельск', 'Россия']}
]
```


```python
# Другой подход
list(filter(lambda visit: 'Россия' in list(visit.values())[0], geo_logs))
```




    [{'visit1': ['Москва', 'Россия']},
     {'visit3': ['Владимир', 'Россия']},
     {'visit7': ['Тула', 'Россия']},
     {'visit8': ['Тула', 'Россия']},
     {'visit9': ['Курск', 'Россия']},
     {'visit10': ['Архангельск', 'Россия']}]




```python
# данный список представляет собой: список со словарями, в которых значения - тоже список
geo_logs_new = []
# Шаг 1. Обращаемся к каждому элементу в списке - словарю
for dict_element in geo_logs:
# Шаг 2. Получаем значения (список) в словаре
    for list_element in dict_element:
        geo_logs_dict_list = dict_element.get(list_element, "Not Found")
# Шаг 3. Если в значениях есть элемент "Россия", то добавляем в новый список
        if geo_logs_dict_list[1] == "Россия":
            geo_logs_new.append(dict_element)
geo_logs_new  
```




    [{'visit1': ['Москва', 'Россия']},
     {'visit3': ['Владимир', 'Россия']},
     {'visit7': ['Тула', 'Россия']},
     {'visit8': ['Тула', 'Россия']},
     {'visit9': ['Курск', 'Россия']},
     {'visit10': ['Архангельск', 'Россия']}]



## Задание 2

Выведите на экран все уникальные гео-ID из значений словаря ids. Т. е. список вида [213, 15, 54, 119, 98, 35]


```python
ids = {'user1': [213, 213, 213, 15, 213], 
       'user2': [54, 54, 119, 119, 119], 
       'user3': [213, 98, 98, 35]}
```


```python
# Вариант 1. Решение на словарях.
unique_ids = set() # set для уникальных значений

for value_list in ids:
    ids_list = ids[value_list]
    for element in ids_list:
        unique_ids.add(element)
print(unique_ids)
```

    {98, 35, 15, 213, 54, 119}
    


```python
# Вариант 2. Решение на списках.
unique_ids_2 = [] # пустой список для уникальных значений

for value_list in ids:
    ids_list = ids[value_list]
    for element in ids_list:
        if element not in unique_ids_2:
            unique_ids_2.append(element)
print(unique_ids_2)
```

## Задание 3

Дан список поисковых запросов. Получить распределение количества слов в них. 
Т. е. поисковых запросов из одного - слова 5%, из двух - 7%, из трех - 3% и т.д.


```python
queries = [
    'смотреть сериалы онлайн',
    'новости спорта',
    'афиша кино',
    'курс доллара',
    'сериалы этим летом',
    'курс по питону',
    'сериалы про спорт',
    'сериалы',
]
```


```python
# Альтернативный вариант подсчета кол-ва слов. Теперь считаем не кол-во пробелов, а слов
target_string = " " # разделитель
output = [] # Задаем список со словами без пробелова
unique_output = set() # set для уникальных значений кол-ва слов
# Составляем список output
for element in queries:
    output.append(len(element.split(" ")))
# Выбираем уникальные варианты кол-ва слов
for value_list in output:
    unique_output.add(value_list)
# Вывод данных
for word_count in unique_output:
    print("Из ", word_count, " слов(а) состоят ", round(output.count(word_count)/ len(output) * 100, 2)," %", sep="")
```

    Из 1 слов(а) состоят 12.5 %
    Из 2 слов(а) состоят 37.5 %
    Из 3 слов(а) состоят 50.0 %
    

## Задание 4

Дана статистика рекламных каналов по объемам продаж. Напишите скрипт, который возвращает название канала с максимальным объемом.
Т. е. в данном примере скрипт должен возвращать 'yandex'.


```python
stats = {'facebook': 55, 'yandex': 120, 'vk': 115, 'google': 99, 'email': 42, 'ok': 98}
```


```python
# добавим расчет максимальной
max_sales = 0
max_sales_channel = ""
for channel in stats:
    #print(stats[channel])
    if  stats[channel] > max_sales:
        max_sales = stats[channel]     
        max_sales_channel = channel
print("Максимальный объем продаж: ", max_sales,"по каналу ", max_sales_channel)
```

    Максимальный объем продаж:  120 по каналу  yandex
    

## Задание 5

н поток логов по количеству просмотренных страниц для каждого пользователя. Список отсортирован по ID пользователя. Вам необходимо написать алгоритм, который считает среднее значение просмотров на пользователя. 
Т. е. надо посчитать отношение суммы всех просмотров к количеству уникальных пользователей.


```python
stream = [
    '2018-01-01,user1,3',
    '2018-01-07,user1,4',
    '2018-03-29,user1,1',
    '2018-04-04,user1,13',
    '2018-01-05,user2,7',
    '2018-06-14,user3,4',
    '2018-07-02,user3,10',
    '2018-03-21,user4,19',
    '2018-03-22,user4,4',
    '2018-04-22,user4,8',
    '2018-05-03,user4,9',
    '2018-05-11,user4,11',
]
```


```python
user_list = set() # set для уникальных id пользователей
value_list = [] # список для просмотров

for element in range(len(stream)):
    user_list.add(stream[element].split(",")[1]) # добавляем в set id пользователя
    value_list.append(int(stream[element].split(",")[2])) # добавляем в список просмотры пользователей
print("Среднее кол-во просмотров на пользователя: ", sum(value_list) / len(user_list), sep="")
```

    Среднее кол-во просмотров на пользователя: 23.25
    

## Задание 6

Дана статистика рекламных кампаний по дням. Напишите алгоритм, который по паре дата-кампания ищет значение численного столбца. 
Т. е. для даты '2018-01-01' и 'google' нужно получить число 25. 
Считайте, что все комбинации дата-кампания уникальны.


```python
stats = [
    ['2018-01-01', 'google', 25],
    ['2018-01-01', 'yandex', 65],
    ['2018-01-01', 'market', 89],
    ['2018-01-02', 'google', 574],
    ['2018-01-02', 'yandex', 249],
    ['2018-01-02', 'market', 994],
    ['2018-01-03', 'google', 1843],
    ['2018-01-03', 'yandex', 1327],
    ['2018-01-03', 'market', 1764],
]
```


```python
data_input = input("Введите дату рекламной компании: ")
chennel_input = input("Введите канал рекламной компании: ")

stats_dict = {}
for element in stats:
    name_list = element[0] + ", " + element[1]
    value = element[2]
    stats_dict[name_list] = value

stats_dict[data_input + ", " + chennel_input]
```

    Введите дату рекламной компании: 2018-01-02
    Введите канал рекламной компании: yandex
    




    249


