# БИБЛИОТЕКА МЕТОДОВ И ФУНКЦИЙ **C#**

## [ОГЛАВЛЕНИЕ](#оглавление)
* [Округление числа после запятой](#округление-числа-после-запятой)
* [Квадратный корень](#квадратный-корень)
* [Возведение в степень](#возведение-в-степень)
* [Ввод Вывод данных - методы Read Write](#ввод-вывод-данных---методы-read-write)
    * [READ](#read---чтение-строки-ввод)
    * [WRITE](#write---написание-строки-вывод)
        * [Форматирование строк](#форматирование-строк)
            * [Представление чисел](#представление-чисел)
            * [Представление даты и времени](#представление-даты-и-времени)
            * [Интерполяция строк - $](#интерполяция-строк)
            * [Управляющие символы (литералы)](#управляющие-символы-литералы)
            * [Класс StringBuilder](#класс-stringbuilder)
* [Длина строки через ToString](#длина-строки-через-tostring)
* [Сокращение ариф. действий](#сокращение-ариф-действий)
* [Арифметические операторы](#арифметические-операторы)
    * [Унарные](#унарные)
    * [Бинарные](#бинарные)
    * [Приоритет и ассоциативность операторов](#приоритет-и-ассоциативность-операторов)
* [Массивы](#массивы)
* [Условные виды методов](#условные-виды-методов)
* [GetNumber](#getnumber-метод)
* [GetArray](#getarray-метод)
* [PrintArray](#printarray-метод)
* [CheckValueArray](#checkvaluearray-метод)
* [SortSelection](#sortselection-метод)
* [SortBubble](#sortbubble-сорт-пузырьком)
* [SortQuick](#sortquick-быстрая)
* [Частота значений](#частота-значений-метод)
* [ToLower проверка](#tolower-проверка)
___
### **Округление числа после запятой**
```C#
Math.Round(value, count)
// value - значение для округления
// count – количество значащих цифр после запятой
```
[оглавление](#оглавление)
___
### **Квадратный корень**
```C#
MathF.Sqrt(value)
// value - значение для преобразования
```
метод преобразует тип данных в **float**

[оглавление](#оглавление)
___
### **Возведение в степень**
```C#
MathF.Pow(x,y)
// x - значение
// y - степень
```
метод преобразует тип данных в **float**

[оглавление](#оглавление)
___
### **Ввод Вывод данных - методы Read Write**
* ### *READ* - чтение строки (ввод)
```C#
Console.Read() // чтение строки с консоли
Console.ReadLine() // чтение строки с переходом на новую строку, с консоли
```
"Задержка" консоли может осуществляться командами:
```C#
Console.Read() // читает клавишу Enter
Console.ReadLine() // читает клавишу Enter
Console.ReadKey() // читает любую клавишу
```
* ### *WRITE* - написание строки (вывод)
```C#
Console.Write() // вывод данных в консоль
Console.WriteLine() // вывод данных с переходом на новую строку, в консоль
```
***Console.WriteLine()*** может использоваться без данных в скобках, просто чтобы сделать перевод строки.
При выводе могут использоваться разные особые символы:
```C#
'\a' // звуковой сигнал
'\f' // перевод страницы
'\n' // новая строка
'\r' // возврат каретки, используется с переносом строки
'\t' // символ горизонтальной табуляции, который вводится при нажатии кнопки Tab
'\v' // символ вертикальной табуляции
'\0' // null, ничего
'\b' // backspace
'\\' // символ обратного слеша
'\"' // символ двойных кавычек
'\'' // символ одинарных кавычек
```
[оглавление](#оглавление)
### ***ФОРМАТИРОВАНИЕ СТРОК***

Под форматированием понимается встраивание в строку различных элементом  **(число, дата и т.п.)**, представленных в заданном формате.

Форматирование можно осуществлять с помощью метода ***ToString*** с передачей в него нужных описателей, метода ***Format***, который, в качестве аргументов, получает строку со специальными вставками, определяющими представление элементов и непосредственно сами элементы.

Несколько примеров с этими методоми:

* **ToString**
```C#
Console.WriteLine(12345.ToString("X"));
```
* **String.Format**
```C#
Console.WriteLine(string.Format("value: {0}", 1.23456));    // 1,23456
Console.WriteLine(string.Format("value: {0:F}", 1.23456));  // 1.235
Console.WriteLine(string.Format("value: {0:d}", 1.23456));  // 07.09.2020
```
* **WriteLine без использования String.Format**
```C#
Console.WriteLine("value: {0}", 1.23456);       // 1,23456
Console.WriteLine("value: {0:F}", 1.23456);     // 1.235
Console.WriteLine("date: {0:d}", DateTime.Now); // 07.09.2020
```
Эта функциональность также доступна для методов 
* StringBuilder.AppendFormat
* TextWriter.WriteLine
* Debug.WriteLine
* методы из Trace, которые выводят текстовые сообщения, например:
    * Trace.TraceError
    * TraceSource.TraceInformation.

Каждый элемент форматирования представляется следующим образом:
```C#
{index,alignment:formatString}
// index – это индекс элемента, которым будет замещена данная конструкция;
// alignment – выравнивание
// formatString – формат
```
Можно и без использования ***alignment***
```C#
{index:formatString}
```
Примеры использования элементов форматирования:
```C#
Console.WriteLine("Only index: {0}", 123); // Only index: 123
Console.WriteLine("Index with alignment: {0,-5}{1,5}", 123, 456); // Index with alignment: 123    456
Console.WriteLine("Index with format: 0x{0:X}", 123); // Index with format: 0x7B
```
[оглавление](#оглавление)
#### **ПРЕДСТАВЛЕНИЕ ЧИСЕЛ**

Для представления используются описатели формата
(список не полный, больше в официальной документации):
```C#
'C' или 'c' Представление валюты.

'D' или 'd' Представление целого числа.

'E' или 'e' Представление числа в экспоненциальном виде.

'F' или 'f' Представление числа в формате с плавающей точкой.

'P' или 'p' Представление процентов, выводит число умноженное на 100 со знаком процента.

'X' или 'x' Шестнадцатеричное представление.

'0' Заместитель нуля.

'#' Заместитель цифры.

'.' Разделитель целой и дробной части.
```
Примеры использования:
```C#
Console.WriteLine("C symbol: {0:C}", 123);          // 123,00 ₽
Console.WriteLine("D symbol: {0:D5}", 123);         // 00123
Console.WriteLine("E symbol: {0:E}", 123456789);    // 1,234568E+008
Console.WriteLine("F symbol: {0:F2}", 123.4567);    // 123,46
Console.WriteLine("P symbol: {0:P}", 0.123);        // 123,46
Console.WriteLine("X symbol: 0x{0:X}", 567);        // 0x237
Console.WriteLine("0 symbol: {0:000.00}", 12.6789); // 012,68
Console.WriteLine("# symbol: {0:##}", 14.6789);     // 15
```
[оглавление](#оглавление)
#### **ПРЕДСТАВЛЕНИЕ ДАТЫ И ВРЕМЕНИ**
(список не полный, более детальную информацию можете найти в официальной документации):
```C#
'd' Сокращенный формат даты

'D' Полный формат даты

'f', 'F' Полный формат даты и времени с коротким (полным) форматом времени

'g', 'G' Общий формат даты и времени с коротким (полным) форматом времени

't' Короткий формат времени

'T' Полный формат времени

'M', 'm' Шаблон дней месяца.

'Y', 'y' Шаблон месяца года.
```
Примеры использования:
```C#
Console.WriteLine("d symbol: {0:d}", DateTime.Now);       // d symbol: 22.03.2023
Console.WriteLine("D symbol: {0:D}", DateTime.Now);       // D symbol: 22 марта 2023 г.
Console.WriteLine("f symbol: {0:f}", DateTime.Now);       // f symbol: 22 марта 2023 г. 19:01
Console.WriteLine("F symbol: {0:F}", DateTime.Now);       // F symbol: 22 марта 2023 г. 19:01:18
Console.WriteLine("g symbol: {0:g}", DateTime.Now);       // g symbol: 22.03.2023 19:01
Console.WriteLine("G symbol: {0:G}", DateTime.Now);       // G symbol: 22.03.2023 19:01:18
Console.WriteLine("t symbol: {0:t}", DateTime.Now);       // t symbol: 19:01
Console.WriteLine("T symbol: {0:T}", DateTime.Now);       // T symbol: 19:01:18
Console.WriteLine("{0:yyyy-MM-dd}", DateTime.Now);        // 2023-03-22
Console.WriteLine("{0:dd/MM/yy}", DateTime.Now);          // 22.03.23
Console.WriteLine("{0:dd/MM/yy HH:mm:ss}", DateTime.Now); // 22.03.23 19:01:18
```
[оглавление](#оглавление)
#### **ИНТЕРПОЛЯЦИЯ СТРОК - `$`**
Начиная с C# 6 появилась возможность строить интерполированную строку, формат которой позволяет более просто, по сравнению с составным форматированием, создавать строки.

Интерполированная строка содержит специальные выражения интерполяции, они похожи на элементы форматирования.

Выражения интерполяции имеют следующий вид:
```C#
{interpolationExpression,alignment:formatString}
// interpolationExpression – элемент, значение, которого будет интегрироваться в строку
// alignment – выравнивание
// formatString – формат
```
Примеры с интерполированной строкой:
```C#
int n1 = 45678;
double d1 = 123.34567;
bool b1 = true;
string sv = "test";
Console.WriteLine($"int val: {n1}, double val: {d1:#.###}");    // int val: 45678, double val: 123,346
Console.WriteLine($"bool val: {b1}, string val: {sv}");         // bool val: True, string val: test
```
[оглавление](#оглавление)
#### **УПРАВЛЯЮЩИЕ СИМВОЛЫ (литералы)**

Управляющие символы позволяют вводить в текст команды управления кареткой и символы, которые имеют специальное назначение (одинарные и двойные кавычки).
Ниже представлена таблица с управляющими символами. [см. выше](#write---написание-строки-вывод)
```C#
\a Звуковой сигнал

\b Возврат на одну позицию

\f Перевод страницы

\n Новая строка

\r Возврат каретки

\t Горизонтальная табуляция

\v Вертикальная табуляция

\0 Пустой символ

\’ Одинарная кавычка

\” Двойная кавычка

\\ Обратная косая черта
```
Пример использования:
```C#
Console.WriteLine("\aName:\t\"John\"\nAge:\t\"27\"");   // Name:   "John"
                                                        // Age:    "27"
```
**`@` – буквальный идентификатор**

Еще один элемент, который можно использовать при создании срок – это буквальный идентификатор ***`@`***.

Если его поставить перед строкой, то она будет интерпретироваться буквально, в ней, escape-последовательности представляются без преобразования.

Пример с буквальным идентификатором:
```C#
Console.WriteLine(@"escape is not work: \a\t\n\x1234");     //escape is not work: \a\t\n\x1234
```
[оглавление](#оглавление)
#### **КЛАСС StringBuilder**

`StringBuilder` следует использовать, если вам нужно собрать строку **из большого набора элементов** через конкатенацию, которая, например, может осуществляется в цикле.
В этом случае использование String может оказаться не эффективным решением.

Если для построения итоговой строки использовать оператор ***+***, как это сделано в примере
```C#
string outString = "";
for(int i = 0; i < 10; i++)
{
   outString += i.ToString() + " - ";
}
Console.WriteLine(outString);   // 0 - 1 - 2 - 3 - 4 - 5 - 6 - 7 - 8 - 9 - 
```
то при выполнении операции ***`+=`*** каждый раз будет создавать новый объект класса String в памяти.

Если количество таких присваиваний будет достаточно большим, то программа может аварийно завершиться из-за нехватки памяти, либо занять ее в очень большом объеме. Это происходит из-за того, что сборщик мусора не будет успевать уничтожать неиспользуемые объекты, которые создаются с большой скоростью.

Более эффективным решением будет использование StringBuilder:
```C#
System.Text.StringBuilder sb = new System.Text.StringBuilder("Hello World! ");
for(int i = 0; i < 10; i++)
{
    sb.Append(i.ToString());
    sb.Append(" - ");
}
string outString = sb.ToString();
Console.WriteLine(outString);   // Hello World! 0 - 1 - 2 - 3 - 4 - 5 - 6 - 7 - 8 - 9 - 
```
В вопросе типа «`string` vs `String Builder`» следует придерживаться рекомендаций разработчиков из Microsoft, а именно:

***`StringBuilder` рекомендуется использовать в следующих случаях:***
* Если предполагается, что код будет вносить неизвестное количество изменений в строку во время разработки
(например, при использовании цикла для сцепления случайного числа строк, содержащих данные, введенные пользователем).

* Если предполагается, что код вносит значительное количество изменений в строку.

Также, можно отметить, что StringBuilder не содержит методов поиска подстрок в строке, поэтому, при выборе между string и StringBuilder стоит обратить внимание и на то, предполагается ли производить в строке большое количество операций поиска.
Если да, то, возможно, стоит отказаться от StringBuilder или же производить необходимые операции поиска перед добавлением строки в StringBuilder.

[оглавление](#оглавление)
___
### **ДЛИНА СТРОКИ ЧЕРЕЗ `ToString`**
Так же о методе ***`ToString`*** [см.выше](#форматирование-строк)
```C#
value.ToString().Length
// value - значение / переменная
// ToString().Length - преобразует значение в строку и указывает количество символов - длину
```
Пример:
```C#
int value = 123;
Console.WriteLine(value.ToString().Length); // 3
```
[оглавление](#оглавление)
___
### **СОКРАЩЕНИЕ АРИФ. ДЕЙСТВИЙ**
Запись типа
```C#
number = number + value
```
имеет короткую запись
```C#
number += value
```
Так же и остальные арифметичские действия
```C#
int number = 0;
number -= 5; // number = number - 5; 
number *= 5; // number = number * 5; 
number /= 5; // number = number / 5;
number %= 5; // number = number % 5;
```
[оглавление](#оглавление)
___
### **АРИФМЕТИЧЕСКИЕ ОПЕРАТОРЫ**
Операторы, выполняющие арифметические операции с операндами числовых типов:
* унарные — `++` (приращение), `--` (уменьшение), `+` (плюс) и `-` (минус);
* бинарные — `*` (умножение), `/` (деление), `%` (остаток от деления), `+` (сложение) и `-` (вычитание).

Эти операторы поддерживаются всеми целочисленными типами и типами с плавающей запятой.

* ### **УНАРНЫЕ**
    * #### **Оператор приращения (инкремента) `++`**
        Оператор инкремента **`++`** увеличивает операнд на 1.
        
        Поддерживается в двух формах:
        * Постфиксный оператор приращения **`х++`**
            ```C#
            int i = 3;
            Console.WriteLine(i);   // 3
            Console.WriteLine(i++); // 3
            Console.WriteLine(i);   // 4
            ```
            Результатом является значение **`х`** перед операцией приращения.
            
            То есть операция приращения происходит **после (пост)** возращения **`х`**.
        * Префиксный оператор приращения **`++х`**
            ```C#
            double a = 1.5;
            Console.WriteLine(a);   // 1.5
            Console.WriteLine(++a); // 2.5
            Console.WriteLine(a);   // 2.5
            ```
            Операция  происходит **перед (пре)** возращением **`х`**.
    * #### **Оператор уменьшения (декремента) `--`**
        Оператор декремента **`--`** уменьшает операнд на 1.
        
        Поддерживается в двух формах:
        * Постфиксный оператор **`х--`**
            ```C#
            int i = 3;
            Console.WriteLine(i);   // 3
            Console.WriteLine(i--); // 3
            Console.WriteLine(i);   // 2
            ```
        * Префиксный оператор **`--х`**
            ```C#
            double a = 1.5;
            Console.WriteLine(a);   // 1.5
            Console.WriteLine(--a); // 0.5
            Console.WriteLine(a);   // 0.5
            ```
    * #### **Операторы унарного плюса и минуса**
        Оператор `+` возвращает значение полученного операнда.
        
        Оператор `-` изменяет знак операнда на противоположный.
        ```C#
        Console.WriteLine(+4);     //  4
        Console.WriteLine(-4);     // -4
        Console.WriteLine(-(-4));  //  4
        ```
* ### **БИНАРНЫЕ**
    * #### __Оператор умножения `*`__
        Вычисляет произведение операндов:
        ```C#
        Console.WriteLine(5 * 2);         // 10
        Console.WriteLine(0.5 * 2.5);     // 1.25
        Console.WriteLine(0.1m * 23.4m);  // 2.34
        ```
    * #### **Оператор деления `/`**
        Делит левый операнд на правый.

        Для операндов ***цельночисленных*** типов результат оператора `/` является целочисленным типом, который равен частному двух операндов, округленному в сторону нуля:
        ```C#
        Console.WriteLine(13 / 5);    //  2
        Console.WriteLine(-13 / 5);   // -2
        Console.WriteLine(13 / -5);   // -2
        Console.WriteLine(-13 / -5);  //  2
        ```
        Чтобы получить частное двух операндов в виде числа ***с плавающей запятой***, используйте тип `float`, `double` или `decimal:`
        ```C#
        Console.WriteLine(13 / 5.0);       // 2.6
        int a = 13;
        int b = 5;
        Console.WriteLine((double)a / b);  // 2.6
        ```
        Для типов `float`, `double` и `decimal` результатом оператора `/` является частное двух операндов:
        ```C#
        Console.WriteLine(16.8f / 4.1f);   // 4.097561
        Console.WriteLine(16.8d / 4.1d);   // 4.09756097560976
        Console.WriteLine(16.8m / 4.1m);   // 4.0975609756097560975609756098
        ```
    * #### **Оператор остатка `%`**
        Вычисляет остаток от деления левого операнда на правый.

        Для **целочисленных операндов** результатом `a % b` является значение, произведенное `a-(a/b)*b`. Знак ненулевого остатка такой же, как и у левого операнда, как показано в следующем примере:
        ```C#
        Console.WriteLine(5 % 4);   //  1
        Console.WriteLine(5 % -4);  //  1
        Console.WriteLine(-5 % 4);  // -1
        Console.WriteLine(-5 % -4); // -1
        ```

        Для операндов типа `float` и `double` результатом **`x % y`** для конечных **`x`** и **`y`** будет значение **`z`**, так что:
        * знак **`z`**, если отлично от нуля, совпадает со знаком **`x`**;
        * абсолютное значение **`z`** является значением, произведенным **`|x| - n * |y|`**, где **`n`** — это наибольшее возможное целое число, которое меньше или равно **`|x| / |y|`, а `|x|` и `|y|`** являются абсолютными значениями **`x`** и **`y`**, соответственно.

        Для операндов `decimal` оператор остатка **`%`** эквивалентен оператору остатка типа `System.Decimal`.
        ```C#
        Console.WriteLine(-5.2f % 2.0f); // -1.2
        Console.WriteLine(5.9 % 3.1);    //  2.8
        Console.WriteLine(5.9m % 3.1m);  //  2.8
        ```
    * #### **Оператор сложения `+`**
        Вычисляет сумму своих операндов:
        ```C#
        Console.WriteLine(5 + 4);       // 9
        Console.WriteLine(5 + 4.3);     // 9.3
        Console.WriteLine(5.1m + 4.2m); // 9.3
        ```
        Кроме того, оператор **`+`** можно использовать для объединения строк и делегатов.
    * #### **Оператор вычитания `-`**
        Вычитает правый операнд из левого:
        ```C#
        Console.WriteLine(47 - 3);      // 44
        Console.WriteLine(5 - 4.3);     // 0.7
        Console.WriteLine(7.5m - 2.3m); // 5.2
        ```
        Кроме того, оператор **`-`** можно использовать для удаления делегатов.
### **Приоритет и ассоциативность операторов**
Арифметические операторы в порядке убывания приоритета:
* Постфиксный инкремент **`x++`** и декремент **`x--`**
* Префиксный инкремент **`++x`** и декремент **`--x`**, унарные операторы **`+`** и **`-`**
* Мультипликативные операторы **`*`**, **`/`**, и **`%`**
* Аддитивные операторы **`+`** и **`-`**

[оглавление](#оглавление)
___
### **МАССИВЫ**
Кратко о создании и заполняемости массива
```C#
int[] array = new int[value]; // value размерность массива при создании
Console.WriteLine(array.Length); // array.Length размерность массива

// Способы определения массива
int[] arr1 = new int[3];
arr[0] = 0;
arr[1] = 1;
arr[2] = 2;

int[] arr2 = new int[3] { 0, 1, 2 };
int[] arr3 = new int[] { 0, 1, 2 };
int[] arr4 = new [] { 0, 1, 2 };
int[] arr5 = { 0, 1, 2 };

// получение элемента массива
Console.WriteLine(arr1[2]);  // 2

// получение элемента массива в переменную
int n = arr1[2];        // 2
Console.WriteLine(n);   // 2


```
```C#
int[,] array = new int[rows, columns];  // [,] обозначает двухмерный массив (простая таблица)
// rows - кол-во строк/рядов
// columns - кол-во столбцов
Console.WriteLine(array.GetLength(0));  // размерность массива - кол-во строк = rows
Console.WriteLine(array.GetLength(1));  // размерность массива - кол-во столбцов = columns
```
```C#
// Способы определения двухмерного массива
int[,] arr1;
int[,] arr2 = new int[2, 3];
int[,] arr3 = new int[2, 3] { { 0, 1, 2 }, { 3, 4, 5 } };
int[,] arr4 = new int[,] { { 0, 1, 2 }, { 3, 4, 5 } };
int[,] arr5 = new [,]{ { 0, 1, 2 }, { 3, 4, 5 } };
int[,] arr6 = { { 0, 1, 2 }, { 3, 4, 5 } };
```
Массивы могут иметь и большее количество измерений.
```C#
int[,,] array = new int[2, 3, 4];
```
Соответственно могут быть и четырехмерные массивы и массивы с большим количеством измерений.

[оглавление](#оглавление)
___
### **УСЛОВНЫЕ ВИДЫ МЕТОДОВ**
1. Ничего не принимают и ничего не возвращают
    ```C#
    void Method1()
    {
        Console.WriteLine("Автор...");
    }
    Method1();
    ```
2. Что-то принимают и ничего не возвращают
    ```C#
    void Method2(string msg)
    {
        Console.WriteLine(msg);
    }
    Method2("Текст сообщения");
    // ИЛИ
    string msg = "Текст сообщения";
    Method2(msg);
    ```
    ```C#
    void Method21(string msg, int count)
    {
        int i = 0;
        while (i < count)
        {
            Console.WriteLine(msg);
            i++;
        }
    }
    Method21("Text", 4);
    Method21(count: 4, msg: "Text new");
    ```
3. Ничего не принимают, что-то возвращают
    ```C#
    int Method3()
    {
        return DateTime.Now.Year;
    }
    int year = Method3();
    Console.WriteLine(year);
    ```
4. Что-то принимают, что-то возвращают
    ```C#
    string Method4(int count, string text)
    {
        int i = 0;
        string result = String.Empty;
        while (i < count)
        {
            result = result + text;
            i++;
        }
        return result;
    }
    string res = Method4(10, " wasd");
    Console.WriteLine(res);
    ```
    С циклом `for`
    ```C#
    string Method4(int count, string text)
    {
        string result = String.Empty;
        for (int i = 0; i < count; i++)
        {
            result = result + text;
        }
        return result;
    }
    string res = Method4(10, " wasd");
    Console.WriteLine(res);
    ```
[оглавление](#оглавление)
___
### **GetNumber МЕТОД**
Получение значения вводимое пользователем
* Самый простой
```C#
int GetNumber(string text)
{
    Console.WriteLine(text);
    int size = int.Parse(Console.ReadLine());
    return size;
}

// ИЛИ

int GetNumber(string text)
{
    Console.WriteLine(text);
    string size = Console.ReadLine();
    return int.Parse(size);
}
```
* С проверкой - число не может быть нулем или пустым
```C#
int GetNumber(string text)
{
    Console.Write(text);
    string size = Console.ReadLine();
    while (String.IsNullOrEmpty(size) || int.Parse(size) == 0) { Console.Write(text); size = Console.ReadLine(); }
    return int.Parse(size);
}
```
* С проверкой - число не может быть нулем или пустым или содержать любые символы кроме цифр
```C#
int GetSize(string text)
{
    Console.WriteLine(text);
    string size = Console.ReadLine();
    while (int.TryParse(size, out _) == false || String.IsNullOrEmpty(size) || int.Parse(size) == 0) { Console.WriteLine(text); size = Console.ReadLine(); }
    return int.Parse(size);
}
```
Например `проверка на пятизначность числа`
```C#
int GetNum(string text)
{
    Console.WriteLine(text);
    int number = int.Parse(Console.ReadLine());
    while (number.ToString().Length < 5 || number.ToString().Length > 5)
    {
        Console.WriteLine("Введите именно 5-тизначное число");
        number = int.Parse(Console.ReadLine());
    }
    return number;
}
```
[оглавление](#оглавление)
___
### **GetArray МЕТОД**
Генерация массива

Самый простой пример
```C#
// для двухмерного массива, генерация случайными числами

int[,] GetArray(int rows, int columns, int min, int max)
{
    int[,] array = new int[rows, columns];
    for (int i = 0; i < rows; i++)
    {
        for (int j = 0; j < columns; j++)
        {
            array[i, j] = new Random().Next(min, max + 1);
        }
    }
    return array;
}
```
[оглавление](#оглавление)
___
### **PrintArray МЕТОД**
Вывод массива в консоль

* Самый простой
```C#
Console.Write(String.Join(", ", array));

// Между значениями массива вставляется значение строки, которую указать в скобках ""
// Значения будут выводится последовательн в одну строку
```

* Простой
```C#
// одномерный массив
void PrintArray(int[] array)
{
    Console.Write("[");
    for (int i = 0; i < array.Length; i++)
    {
        if (i != (array.Length - 1)) Console.Write($"{array[i]}, ");
        else Console.Write($"{array[i]}]");
    }
}

```
```C#
// двухмерный массив
void PrintArray(int[,] array)
{
    Console.WriteLine();
    for (int i = 0; i < array.GetLength(0); i++)
    {
        for (int j = 0; j < array.GetLength(1); j++)
        {
            Console.Write("{0,3:00}", array[i, j]);
        }
        Console.WriteLine();
    }
    Console.WriteLine();
}

// {0,3:00} - 0 указывает, что будет выводится array[i, j],
// 3 - количество пробелов после начала вывода значения,
// :00  - формат вывода числа, т.е. 1 будет выводится как 01, если сделать :000, то 1 будет как 001
// можно указать и просто как {0,3}
```
```C#
// двухмерный массив
void PrintArray(int[,] array)
{
    Console.WriteLine();
    for (int i = 0; i < array.GetLength(0); i++)
    {
        for (int j = 0; j < array.GetLength(1); j++)
        {
            Console.Write("{0,4}", array[i, j].ToString(" "));
        }
        Console.WriteLine();
    }
    Console.WriteLine();
}

// array[i, j].ToString(" ") - преобразует значение массива в строку со значением указанным в "", в данном случае пробел
// array[i, j].ToString() - можно и не указывать значение, тогда значение просто преобразуется в строку
```
```C#
Console.Write(array[i, j] + $"\t");
// Выведет значение и добавит табуляцию - 4 пробела, после значения
```
[оглавление](#оглавление)
___
### **CheckValueArray МЕТОД**
Метод проверки на наличие определенного числа в массиве
```C#
// В данном случае проверка в трехмерном массиве
int CheckValueArray(int[,,] array, int number)
{
    int count = 0;
    for (int k = 0; k < array.GetLength(2); k++)
    {
        for (int i = 0; i < array.GetLength(0); i++)
        {
            for (int j = 0; j < array.GetLength(1); j++)
            {
                if (array[i, j, k] == number)
                {
                    count++;
                }
            }
        }
    }
    return count;
}
// для двухмерного массива нужно удалить один цикл
```
далее в следующем методе нужно вставить строки
```C#
// строки для трехмерного массива
array[i, j, k] = new Random().Next(min, max + 1);
count = CheckValueArray(array, array[i, j, k]);
while (count > 1)
{
    array[i, j, k] = new Random().Next(min, max + 1);
    count = CheckValueArray(array, array[i, j, k]);
}
// для двухмерного нужно использовать array[i, j] вместо array[i, j, k]
```
Например если вставить их в метод GetArray
```C#
int[,] GetArray(int rows, int columns, int min, int max)
{
    int[,] array = new int[rows, columns];
    for (int i = 0; i < rows; i++)
    {
        for (int j = 0; j < columns; j++)
        {
            array[i, j] = new Random().Next(min, max + 1);
            count = CheckValueArray(array, array[i, j]);
            while (count > 1)
            {
                array[i, j] = new Random().Next(min, max + 1);
                count = CheckValueArray(array, array[i, j]);
            }
        }
    }
    return array;
}
```
То есть, если при новом сгенерированном элементе массива при проверке **`count`** будет **`больше 1`**, то будет выполняться цикл **`while`**, пока вновь сгенерированное число не будет уникальным.

Почему **`count > 1`**, потому что при проверке значение найдет само себя и присвоит `1`, но если будет больше 1 значит есть еще одно такое же число.

[оглавление](#оглавление)
___
### **SortSelection МЕТОД**
Сортировка чисел от наименьшего к большему или наоборот.
```C#
// Двухмерный массив

// В данном случае сортивка по строке от наибольшего к меньшему

void SortSelection(int[,] array)
{
    for (int i = 0; i < array.GetLength(0); i++)
    {
        for (int index = 0; index < array.GetLength(1); index++)
        {
            int maxIndex = index;
            for (int j = index; j < array.GetLength(1); j++)
            {
                if (array[i, j] > array[i, maxIndex])
                {
                    maxIndex = j;
                }
            }
            int temporary = array[i, index];
            array[i, index] = array[i, maxIndex];
            array[i, maxIndex] = temporary;
        }
    }
    Console.WriteLine();
}
// Чтобы сделать от наименьшего к большему, нужно в операторе if  поменяьб > на <
// и поменять синтаксис в коде, вместо max указать min
```
```C#
// Для одномерного массива

// В данном случае как раз сортировка от наименьшего к большему

void SortSelection(int[] array)
{
    for (int i = 0; i < array.Length; i++)
    {
        int minPosition = i;
        for (int j = i + 1; j < array.Length; j++)
        {
            if (array[j] < array[minPosition])
            {
                minPosition = j;
            }
        }
        int temporary = array[i];
        array[i] = array[minPosition];
        array[minPosition] = temporary;
    }
    Console.WriteLine();
}
```
[оглавление](#оглавление)
___
### **SortBubble СОРТ ПУЗЫРЬКОМ**
Сортировка путем сравнения 2х смежных значений в массиве и перестановке их при соблюдении условий (мин макс или макс мин).
* Базовая
```C#
public static int[] SortBubble(this int[] collection)
{
int size = collection.Length;

for (int current = 0; current < size - 1; current++)
{
    for (int i = 0; i < size - 1; i++)
    {
        if (collection[i] > collection[i + 1])
        {
            int temp = collection[i];
            collection[i] = collection[i + 1];
            collection[i + 1] = temp;
        }
    }
}
return collection;
}
```
* Оптимизированная
```C#
public static int[] SortBubbleOptimized(this int[] collection)
{
    int size = collection.Length;
    for (int current = 0; current < size - 1; current++)
    {
    for (int i = 0; i < size - 1 - current; i++)
    {
        if (collection[i] > collection[i + 1])
        {
            int temp = collection[i];
            collection[i] = collection[i + 1];
            collection[i + 1] = temp;
        }
    }
}
return collection;
}
```

[оглавление](#оглавление)
___
### **SortQuick БЫСТРАЯ**
```C#
public static class Sorting
{
  public static int[] SortQuick(this int[] collection, int left, int right)
  {
    int i = left;
    int j = right;

    int pivot = collection[Random.Shared.Next(left, right)];
    while (i <= j)
    {
      while (collection[i] < pivot) i++;
      while (collection[j] > pivot) j--;

      if (i <= j)
      {
        int t = collection[i];
        collection[i] = collection[j];
        collection[j] = t;
        i++;
        j--;
      }
    }
    if (i < right) SortQuick(collection, i, right);
    if (left < j) SortQuick(collection, left, j);
    return collection;
  }
}
```

[оглавление](#оглавление)
___
### **ЧАСТОТА ЗНАЧЕНИЙ МЕТОД**
Метод позволяет найти сколько раз определенное число есть в массиве
```C#
Console.Clear();

int FindDigit(int[,] array, int digit)
{
    int[,] countArray = new int[(array.GetLength(0) * array.GetLength(1)), 2];
    int count = 0;
    for (int i = 0; i < array.GetLength(0); i++)
    {
        for (int j = 0; j < array.GetLength(1); j++)
        {
            if (array[i, j] == digit)
            {
                count++;
            }
        }
    }
    return count;
}

int[,] FreqDigit(int[,] array)
{
    Console.WriteLine();
    int[,] countArray = new int[(array.GetLength(0) * array.GetLength(1)), 2];
    for (int i = 0; i < array.GetLength(0); i++)
    {
        for (int j = 0; j < array.GetLength(1); j++)
        {
            countArray[(i + j + (i * (array.GetLength(1) - 1))), 0] = array[i, j];
            countArray[(i + j + (i * (array.GetLength(1) - 1))), 1] = FindDigit(array, array[i, j]); 
        }
    }
    return countArray;
}

void CheckValueArray(int[,] array)
{
    for (int i = 0; i < array.GetLength(0); i++)
    {
        int count = 0;
        if (i == 0)
        {
            Console.WriteLine("{0} встречается {1} раз(а)", array[i, 0], array[i, 1]);
            continue;
        }
        for (int k = 0; k < i; k++)
        {
            if (array[k, 0] == array[i, 0])
            {
                count++;
                continue;
            }
        }
        if (count != 0) continue;
        else Console.WriteLine("{0} встречается {1} раз(а)", array[i, 0], array[i, 1]);
    }
}

void PrintArray(int[,] array)
{
    Console.WriteLine();
    for (int i = 0; i < array.GetLength(0); i++)
    {
        for (int j = 0; j < array.GetLength(1); j++)
        {
            Console.Write(array[i, j] + $"\t");
        }
        Console.WriteLine();
    }
}

int[,] GetArray(int rows, int columns, int min, int max)
{
    int[,] array = new int[rows, columns];
    for (int i = 0; i < rows; i++)
    {
        for (int j = 0; j < columns; j++)
        {
            array[i, j] = new Random().Next(min, max + 1);
        }
    }
    return array;
}

int GetSize(string text)
{
    Console.WriteLine(text);
    string size = Console.ReadLine();
    while (int.TryParse(size, out _) == false || String.IsNullOrEmpty(size) || int.Parse(size) == 0) { Console.WriteLine(text); size = Console.ReadLine(); }
    return int.Parse(size);
}

int sizeRow = GetSize("Введите кол-во строк ");
int sizeColumn = GetSize("Введите кол-во столбцов ");
int[,] array = GetArray(sizeRow, sizeColumn, 0, 100);
PrintArray(array);
int[,] countArray = FreqDigit(array);
CheckValueArray(countArray);
```
[оглавление](#оглавление)
___
### **ToLower ПРОВЕРКА**
ToLower переводит все символы в нижний регистр, например уйдет проблема того как пользователь введет свое имя
```C#
Console.Write("Введите имя пользователя: ");
string username = Console.ReadLine();

if(username.ToLower()=="маша")
{
    Console.WriteLine("Ура, это же МАША!!!");
}
else
{
    Console.Write("Привет, ");
    Console.Write(username);
    Console.WriteLine("!");
    // ИЛИ
    Console.WriteLine("Привет, {0}!", username);
}
```
[оглавление](#оглавление)
___
