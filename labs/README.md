Множества

Множество в языке Питон — это структура данных, эквивалентная множствам в математике. Множество может состоять из различных элементов, порядок элементов в множестве неопределен. В множество можно добавлять и удалять элементы, можно перебирать элементы множества, можно выполнять операции над множествами (объединение, пересечение, разность). Можно проверять принадлежность элементу множества.

В отличии от массивов, где элементы хранятся в виде последовательного списка, в множествах порядок хранения элементов неопределен (более того, элементы множества храняться не подряд, как в списке, а при помощи хитрых алгоритмов). Это позволяет выполнять операции типа “проверить принадлежность элемента множеству” быстрее, чем просто перебирая все элементы множества.

Элементами множества может быть любой неизменяемый тип данных: числа, строки, кортежи. Изменяемые типы данных не могут быть элементами множества, в частности, нельзя сделать элементом множества список (но можно сделать кортеж) или другое множество. Требование неизменяемости элементов множества накладывается особенностями представления множества в памяти компьютера.
Задание множеств

Множество задается перечислением всех его элементов в фигурных скобках. Например:

A = {1, 2, 3}

Исключением явлеется пустое множество, которое можно создать при помощи функции set(). Если функции set передать в качестве параметра список, строку или кортеж, то она вернет множество, составленное из элементов списка, строки, кортежа. Например:

A = set('qwerty')
print(A)

выведет {'e', 'q', 'r', 't', 'w', 'y'}.

Каждый элемент может входить в множество только один раз, порядок задания элементов не важен. Например, программа:

A = {1, 2, 3}
B = {3, 2, 3, 1}
print(A == B)

выведет True, так как A и B — равные множества.

Каждый элемент может входить в множество только один раз. set('Hello') вернет множество из четырех элементов: {'H', 'e', 'l', 'o'}.
Работа с элементами множеств

Узнать число элементов в множестве можно при помощи функции len.

Перебрать все элементы множества (в неопределенном порядке!) можно при помощи цикла for:

C = {1, 2, 3, 4, 5}
for elem in C:
    print(elem)

Проверить, принадлежит ли элемент множеству можно при помощи операции in, возвращающей значение типа bool:

i in A

Аналогично есть противоположная операция not in.

Для добавления элемента в множество есть метод add:

A.add(x)

Для удаления элемента x из множества есть два метода: discard и remove. Их поведение различается только в случае, когда удаляемый элемент отсутствует в множестве. В этом случае метод discard не делает ничего, а метод remove генерирует исключение KeyError.

Наконец, метод pop удаляет из множества один случайный элемент и возвращает его значение. Если же множество пусто, то генерируется исключение KeyError.

Из множества можно сделать список при помощи функции list.
Перебор элементов множества

При помощи цикла for можно перебрать все элементы множества:

Primes = {2, 3, 5, 7, 11}
for num im Primes:
    print(num)
/////////////////////
java
TreeSet

Обобщенный класс TreeSet<E> представляет структуру данных в виде дерева, в котором все объекты хранятся в отсортированном виде по возрастанию. TreeSet является наследником класса AbstractSet и реализует интерфейс NavigableSet, а следовательно, и интерфейс SortedSet.

В классе TreeSet определены следующие конструкторы:

    TreeSet(): создает пустое дерево

    TreeSet(Collection<? extends E> col): создает дерево, в которое добавляет все элементы коллекции col

    TreeSet(SortedSet <E> set): создает дерево, в которое добавляет все элементы сортированного набора set

    TreeSet(Comparator<? super E> comparator): создает пустое дерево, где все добавляемые элементы впоследствии будут отсортированы компаратором.

TreeSet поддерживает все стандартные методы для вставки и удаления элементов:
1
2
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
20
21
22
23
24
	
import java.util.TreeSet;
 
public class Program{
      
    public static void main(String[] args) {
          
        TreeSet<String> states = new TreeSet<String>();
          
        // добавим в список ряд элементов
        states.add("Germany");
        states.add("France");
        states.add("Italy");
        states.add("Great Britain");
        
        System.out.printf("TreeSet contains %d elements \n", states.size());
         
        // удаление элемента
        states.remove("Germany");
        for(String state : states){
          
            System.out.println(state);
        }
    }
}

И поскольку при вставке объекты сразу же сортируются по возрастанию, то при выводе в цикле for мы получим отсортированный набор:

TreeSet contains 4 elements
France
Great Britain
Italy

Так как TreeSet реализует интерфейс NavigableSet, а через него и SortedSet, то мы можем применить к структуре дерева различные методы:
1
2
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
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
	
import java.util.*;
 
public class Program{
      
    public static void main(String[] args) {
          
        TreeSet<String> states = new TreeSet<String>();
          
        // добавим в список ряд элементов
        states.add("Germany");
        states.add("France");
        states.add("Italy");
        states.add("Spain");
        states.add("Great Britain");
        
        System.out.println(states.first()); // получим первый - самый меньший элемент
        System.out.println(states.last()); // получим последний - самый больший элемент
        // получим поднабор от одного элемента до другого
        SortedSet<String> set = states.subSet("Germany", "Italy");
        System.out.println(set);
        // элемент из набора, который больше текущего
        String greater = states.higher("Germany");
        // элемент из набора, который меньше текущего
        String lower = states.lower("Germany");
        // возвращаем набор в обратном порядке
        NavigableSet<String> navSet = states.descendingSet();
        // возвращаем набор в котором все элементы меньше текущего
        SortedSet<String> setLower=states.headSet("Germany");
        // возвращаем набор в котором все элементы больше текущего
        SortedSet<String> setGreater=states.tailSet("Germany");  
        System.out.println(navSet);
        System.out.println(setLower);
        System.out.println(setGreater);
    }
}
//////////////////
c++
Линейный односвязный 

Каждый узел однонаправленного (односвязного) линейного списка (ОЛС) содержит одно поле указателя на следующий узел. Поле указателя последнего узла содержит нулевое значение (указывает на NULL).
struct inform{};//информационная структура
struct List1
{
inform inf;
List1*pNext;
};
Основные функции 
1. Добавить в начало
2. Добавить в конец 
3.Добавить после/перед заданным
4.Извлечь из начала 
....

Линейный кольцевой список 
это список, у которого последний элемент связан с первым. Кольцевой список можно сделать как односвязным, так и двухсвязным. Рассмотрим вкратце односвязный кольцевой список.
struct List2
{
inform inf;
List2*pNext;
List2*pPred;
};
Основные функции
1.Добавить в начало/ в конец 
2.Добавить после заданного 
3. Извлечь из начала
4.Извлечь произвольный элемент 
