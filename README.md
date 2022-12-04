# JVM
```java
/* 1. Загрузка класса JvmComprehension  с помощью ClassLoading
   2. Загрузка классов AplicationClassLoader->PlatformClassLoader-->BootstrapClassLoader
   3. Подготовка классов к выполнению Linking(Verify->Prepare->Resolve)
   4. Инициализация (Initialozation)
*/
   public class JvmComprehension {
// 5. В момент вызова метода main создаётся фрейм в Stack Memory, heap (куча) - пустая, Metaspace.
    public static void main(String[] args) {
       // 6. В стек Stack Memory добавляются int i = 1
       int i = 1;                      // 1
       // 7.В heap добавляется Object, также в Stack Memory добавляется название переменной
        Object o = new Object();        // 2
        // 6. В Stack Memory добавляются int ii = 2
        Integer ii = 2;                 // 3
        // 7. В Stack Memory добавляется фрейм printAll
        // 8. В фрейме printAll создаются переменные o, i, ii и связываются с heap 
        printAll(o, i, ii);             // 4
        // 9. Создаётся новый фрейм в стеке, куда передаётся ссылка на String
        System.out.println("finished"); // 7
    }

    private static void printAll(Object o, int i, Integer ii) {
    // 9.1 В heap создается объект Integer, также в фрейме printAll создается uselessVar со связью на объект Integer из heap
        Integer uselessVar = 700;                   // 5
    // 9.2. Cоздается новый фрейм в Stack Memory, куда передаются ссылки на o, i, ii
    // 9.3. Создается новый фрейм в Stack Memory, куда передается String
        System.out.println(o.toString() + i + ii);  // 6
    }
}
```
