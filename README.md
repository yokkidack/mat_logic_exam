# mat_logic_exam

## 21) Класс PSPASE и игра двух лиц. Теорема о соотношении между ними. (8-10 баллов)

### Теорема 9.5. ###
Задача Z лежит в классе PSPACE тогда и только тогда, когда существует игра с полиномиальным от длины входа числом ходов и полиномиально вычислимым результатом такая, что LZ=Lw.

### Доказательство. ###
Пусть число ходов ограничено полиномом q(n), а длина каждого записываемого игроками слова ограничена полиномом p(n). Алфавит A  конечен |A|=k. Поэтому число всех возможных слов тоже конечно. 
Сначала докажем, что игра с полиномиальным от длины входа числом ходов и полиномиально вычислимым результатом лежит в классе PSPACE. 
Построим следующее корневое дерево T. Его корнем будет I. Затем последовательно идут ярусы, соответствующие ходам первого и второго игрока. На каждом ярусе расположены вершины, соответствующие всем возможным ходам игрока.
 Каждой вершине можно приписать метку w  или b в зависимости от того, кто в данной вершине имеет выигрышную стратегию. По эти меткам можно определить. Кто имеет выигрышную стратегию на всем дереве, т. е. на входе I.
Метки расставляются следующим способом. Каждому листу дерева, а это узлы яруса yq(n) (или xq(n), если нет последнего хода черных) однозначно сопоставлено значение предиката. Если предикат принимает истинное значение, то пометкой будет w, в противном случае - b. Затем поочередно рассматриваем узлы яруса xq(n) и вершине приписываем пометку w, если все ее дети имеют пометку w. В противном случае ставим пометку b. По этому правилу помечаем все ярусы, соответствующие ходам первого игрока. Вершины ярусов, соответствующие ходам второго игрока, помечаем следующим образом. Если среди детей есть хотя бы одна, помеченная как w, то пометкой будет w. В противном случае -  b. По этим пометкам однозначно восстанавливается исход игры на входе I. Таким образом, для решения задачи Z нужно построить МТ, моделирующую вышеприведенный процесс расстановки пометок и вычисления значений предиката на листьях дерева. Число вершин в дереве полиномиально, полиномиально и время одной проверки значения предиката. Поэтому данная МТ требует O(p(n)q(n)) ячеек памяти. В одну сторону теорема доказана.
Пусть теперь есть некоторая задача Z в классе PSPACE. Покажем теперь, что существует игра с полиномиальным от длины входа числом ходов и полиномиально вычислимым результатом такая, что LZ=Lw.
Итак, у нас есть МТ, распознающая на полиномиальной памяти вхождение слова в язык LZ. Пусть размер памяти p(x). Построим допускающую таблицу такой машины. Как бы не заполняли такую таблицу в конечном алфавите A, |A|=h, с множеством состоянийS, |S|=s, разных таблиц будет не более (h+s)p(x)p(x). Поэтому можно считать, что время работы МТ ограничено экспонентой 2q(x), где q(x) — некоторый полином, а допускающая таблица имеет q(x) столбцов и 2q(x) строк.

Игра состоит в следующем. Задан вход I. Белые утверждают, что на этом слове МТ дает ответ "да". Черные хотят проверить. Первым ходом белые записывают состояние МТ после 2q(x) тактов работы. Черные своим ходом выбирают один из двух промежутков: от начала до 2q(x)–1 -го такта или от 2q(x)–1-го такта до конца. В середине выбранного черными промежутка белые вновь декларируют состояние МТ, черные выбирают одну из половинок этого промежутка. Игра заканчивается за O(q(n)) шагов в тот момент. Когда длина промежутка стала равной единице, т.е. он содержит два последовательных состояния. Если между этими состояниями существует корректный переход в данной МТ, то выиграли белые, в противном случае выигрывают черные.
Если действительно на входе I ответ МТ "да", то белые гарантируют выигрыш, постоянно говоря правду. В противном случае, где-то есть неправильный переход, а черным нужно его указать. Они это обязательно сделают.
Теорема доказана.

## 22) Сформулировать теорему о длине формул в исчислении предикатов в общем виде и в предваренной (приведенной) нормальной форме. (8-10 баллов)

### Опр. ### 
Формула исчисления предикатов следующего вида: F=Qx1Q2x2…QnxnG, где Qx1, Q2x2,…,Qnxn – кванторы, а формула G не содержит кванторов, называется формулой в предваренной (приведенной) нормальной форме.
Просто из определения логических функций (конъюнкции, дизъюнкции, импликации и отрицания) сразу следует утверждение.
### Теорема. ###
Для каждой формулы логики предикатов длины L в нормальной форме со связками (не,→) существует логически эквивалентная (равносильная) ей формула в нормальной форме со связками (не, и, или), имеющая длину constL.


## 23) Дать определение РАМ (Равнодоступная Адресная Машина) и РАСП. Привести пример РАМ (или построить программу вычисления заданной преподавателем функции). (8-10 баллов)

Равнодоступная адресная машина (РАМ) представляет собой усложнение МТ. `TODO: add pic` 

- Вместо одной ленты и головки имеются две: 
- - входная, с которой можно только читать, 
- - и выходная, предназначенная для записи. 
- Вычисления производятся в сумматоре. 
- РАМ имеет также неограниченный объем памяти в виде последовательности перенумерованных ячеек.

Работой лент, сумматора, головок управляет `программа`, состоящая из перенумерованной последовательности команд. Наличие счетчика команд позволяет расставлять метки в программе.
Программа для РАМ не записывается в память, поэтому предполагается, что `программа не изменяет сама себя`.

Все вычисления происходят в первом регистре, называемом сумматором.
Команда состоит из кода операции и адреса. Это известно всем, кто программировал на языке ассемблера. Операнд команды может задаваться тремя способами. 
 - В виде целого числа (литерала) i, что соответствует команде присвоения в программе. Это записывается как =i .
- Либо в адресе команды содержится адрес регистра, в котором лежит значение операнда. Здесь  i – содержимое регистра, 
- Либо в адресе команды содержится адрес регистра (указатель), в котором содержится адрес регистра, содержащего значение операнда. Здесь `*I` означает косвенную адресацию. В случае отрицательного адреса программа останавливается.

Счетчик команд  вначале установлен на первую команду в программе P, выходная лента пустая, содержимое c(i)=0 для любого регистра i. После выполнения k-й команды  P счетчик команд переходит на (k+1)-ю команду, если это не была команда условного перехода. (См. пример ниже).
Чтобы описать действия команды, задаются значения v(a) операнда a.
 - v(=i)=i.
 - v(i)=c(i).
 - v(*i)=c(c(i)).
Меняя набор типов команд, можно говорить не о РАМ, а о разных формальных схемах алгоритма, принадлежащих к определенному типу. Но все они содержат некоторый набор базовых операций, поэтому можно считать, что программирование на них имеет одинаковую сложность.
Пусть набор типов команд фиксирован. Тогда алгоритм решения некоторой задачи в данном формализме включает в себя входной и выходной алфавит, а также текст программы. 

Приведем PAM в качестве примера. Это команды начала работы и останова, команды чтения и письма, четыре арифметические операции, команда хранения, команда перехода на метку и две команды условного перехода в зависимости от содержимого сумматора.

| Команда  | Действие  |
|---|---|
| LOAD a | `c(0) ← v(a)`  |
| STORE(i), STORE(`*i`)  | `c(i) ← c(0), c(c(i)) ← c(0)`  |
| ADD(a)  | `c(0) ← c(0)+v(a)`  |
| SUB(a)  | `c(0) ← c(0)-v(a)`  |
| MULT(a)  | `c(0) ←c(0)v(a)`  |
| DIV(a)  | `c(0) ←[c(0)/v(a)]`  |
| READ(i), READ(`*i`)  | `c(i) ←  очередной входной символ, c(c(i)) ← очередной входной символ. Головка входной ленты сдвигается на клетку вправо.`  |
| WRITE(a)  | `v(a) печатается в клетке выходной ленты, которую на данный момент обозревает головка выходной ленты. Головка выходной ленты сдвигается на клетку вправо.`  |
| JUMP(b)  | `Счетчик команд устанавливается на команду с меткой b.`  |
| JGTZ(b)  | `Если c(0)>0, то счетчик команд устанавливается на команду с меткой b, в противном случае – на следующую команду.`  |
| JZERO(b)  | `Если c(0)=0, то счетчик команд устанавливается на команду с меткой b, в противном случае – на следующую команду.`  |
| HALT  | `Работа программы прекращается.`  |

## 24) Двуместные отношения и сводимость по Тьюрингу. NP-трудные задачи. Привести пример. (6-8 баллов

## 25) Дать определения и привести примеры следующих понятий в исчислении предикатов: Предикат. Формула в исчислении предикатов. Выполнимые и общезначимые формулы. Приведенная нормальная форма. (6-8 баллов)

Опр. `n-местный предикат` – это отношение на декартовом произведении n множеств.

Опр. `Одноместный предикат` – это свойство. 

Опр. `Формулы логики` предикатов определяются следующим образом:
а)	всякая элементарная формула есть формула;
б)	если А и В - формулы и х - предметная переменная, то каждое из выражений (А), (А→В), (хА) есть формула;
в)	выражение является формулой только в том случае, если это следует из правил а) и б).


Опр. Формула логики предикатов называется логически `общезначимой`, если она истинна в любой интерпретации.

Логическая общезначимость формулы означает, что какую бы ни выбирали область интерпретации и какие бы соответствия не задавали, мы всегда будем получать истинные отношения или высказывания.
Примером логически общезначимых формул, очевидно, являются следующие формулы: xA→ хА ; xA ≈ хА .

Опр. Формула логики предикатов A называется `выполнимой`, если существует интерпретация, в которой выполнима A.

Примером выполнимой формулы является приведенная выше формула xA(x,y,b1).

Опр. Формула исчисления предикатов следующего вида: F=Qx1Q2x2…QnxnG, где Qx1, Q2x2,…,Qnxn – кванторы, а формула G не содержит кванторов, называется `формулой в предваренной (приведенной) нормальной форме`.

## 26) Определить классы сложности для задач, данных преподавателем. (6-8 баллов)

## 27) Сформулировать определения НАМ, МТ, РАМ, РАСП и теоремы о соотношении сложности вычисления в этих моделях. (8-10 баллов)

- НАМ
- МТ
- РАМ Равнодоступная адресная машина (РАМ) представляет собой усложнение МТ. `TODO: add pic` 
~~~
- Вместо одной ленты и головки имеются две: 
- - - входная, с которой можно только читать, 
- - и выходная, предназначенная для записи. 
- Вычисления производятся в сумматоре. 
- РАМ имеет также неограниченный объем памяти в виде последовательности перенумерованных ячеек.
Работой лент, сумматора, головок управляет `программа`, состоящая из перенумерованной последовательности команд. Наличие счетчика команд позволяет расставлять метки в программе.
Программа для РАМ не записывается в память, поэтому предполагается, что `программа не изменяет сама себя`.
~~~
- РАСП Равноадресная доступная машина с хранимой программой (РАСП) отличается от РАМ тем, что ее программа хранится в памяти. Каждая команда занимает два регистра памяти, в первом хранится код команды, во втором - адрес.


## 28) Понятие алгоритма. Понятие эквивалентность алгоритмов. Тезис Черча. (4-6 баллов)

### Алгоритм
- это общая, выполняемая шаг за шагом процедура решения задачи. 

### Эквивалентность алгоритмов
Рассмотрим два алгоритма ℑ и ℜ над алфавитом A. 
Если ℑ(P)≈ℜ(P) для любого слова P в алфавите A, то эти алгоритмы называются вполне эквивалентными относительно A. 
Если ℑ(P)≈ℜ(P) для любого слова P в алфавите A такого, что хотя бы одно из выражений ℑ(P) или ℜ(P) определено и является словом в алфавите A, то эти алгоритмы называются эквивалентными относительно A. 

### Тезис Черча
Согласно тезису Черча `любые две формальные схемы, описывающие понятие алгоритма должны быть эквивалентны друг другу`.

## 29) Теорема об алгоритмической неразрешимости проблемы остановки для МТ. (8-10 баллов)

Приведем пример, который, по сути, является известным со времен античности парадоксом брадобрея. В деревне есть брадобрей, который бреет всех, кто не бреется сам. Попробуйте ответить на вопрос, бреет ли он самого себя. При любом ответе получается противоречие.
Облачим теперь этот парадокс в «математическую форму». Проблема остановки (halting problem) состоит в том, чтобы ответить на вопрос (мы о нем говорили выше, когда давали определение машины Тьюринга): остановится или зациклится данная машина Тьюринга T на данном входе x? Оказывается, что, как и в случае брадобрея, любой ответ приводит к противоречию. То есть не существует машины Тьюринга, которая решает проблему остановки.
### Теорема. 
Проблема остановки алгоритмически неразрешима.
### Доказательство.
От противного. Пусть такая машина T* существует. Тогда на входе (T,x) она выдает ответ «да», если машина Т останавливается на этом входе, и «нет» в противном случае. (Здесь Т – слово в алфавите А, являющееся описанием машины Т). Тогда по Т* можно построить машину Тьюринга T’(x), которая в случае, если T*(x,x)=”да”, начинает двигать головку в одну сторону и зацикливается, а в случае T*(x,x)=”нет” она останавливается. Что в этом случае будет означать T’(T’)? Остановится или нет машина на этом входе? Если «да», то это означает, что T*(T’)= «нет», т.е. T’ не должна останавливаться на T’. Если «нет», то это означает, что T*(T’)= «да», т.е. T’  должна останавливаться на T’.
Получили противоречие
Теорема доказана.


## 30) Классы NP и co-NP. Соотношение между ними. Теорема об NP–полной задаче и классе Co-NP. (8-10 баллов)

Класс NP - это класс языков, допускаемых НМТ за полиномиальное время. (То есть эта НМТ, во-первых, допускает язык, а, во-вторых, время ее работы ограничено полиномом.)

Определение. Задача из NP называется NP-полной, если к ней полиномиально сводится любая задача из NP.
Класс NP-полных задач обозначается через NPC.

### TODO: Теорема об NP–полной задаче и классе Co-NP.
