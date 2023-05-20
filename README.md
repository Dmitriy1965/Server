# Server


При запуске приложения  при помощи подсистемы загрузчиков 
классов СlassLoader загружаются в область памяти Metaspace классы:

* JvmComprehension
* Integer
*  System

Далее происходит подготовка классов к выполнению

*  проверка, что код валиден
*  подготовка примитивов в статических полях
*  связывание ссылок на другие классы


При успешном выполнении проходит инициализация 



public class JvmComprehension {

    public static void main(String[] args) {

                                                     Создание в стеке фрейма "main"


        int i = 1;                      // 1    Создание в фрейме "main" переменной "i"
                                                со значением "1" 

        Object o = new Object();        // 2    Выделение в HEAP  участка памяти для 
                                                "Object" и передача ссылки на адрес в переменную
                                                "o" в стеке.фрейм.main  
        Integer ii = 2;                 // 3    Выделение в HEAP  участка памяти для 
                                                "Integer" и передача ссылки на адрес в переменную
                                                "ii" в стеке.фрейм.main

       printAll(o, i, ii);              // 4    Создание в стеке фрейма "printAll"  и запись
						в него переменных "o", "i", "ii"

        System.out.println("finished"); // 7    Создание в стеке фрейма "println"
						  Закрытие фрейма
						уборщик мусора освобождает память HEAP
    }
							Создание в стеке фрейма "printAll"

    private static void printAll(Object o, int i, Integer ii) {

        Integer uselessVar = 700;         // 5   Выделение в HEAP  участка памяти для 
                                                "Integer" со значением "700"  и передача 
						 ссылки в переменную
                                                "uselessVar" в стеке.фрейм.printAll


        System.out.println(o.toString() + i + ii);  // 6  Создание в стеке фрейма "toString"
							  Закрытие фрейма
							Создание в стеке фрейма "println"
							  Закрытие фрейма
							уборщик мусора освобождает память HEAP
    }
}
