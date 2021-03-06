## 컬렉션프레임워크

- 자바에서 이야기를 하는 프레임워크는 "잘 정의된 구조의 클래스들"이라고 이야기를 할 수 있다.![](/Users/jaeyeonkim/Desktop/collection1.png)


#### List\<E> 인터페이스를 구현하는 컬렉션 클래스들

- ArrayList\<E> : 배열 기반 자료구조, 배열을 이용하여 자료를 저장
- LinkedList\<E> : 리스트 기반 자료구조, 리스트를 구성하여 인스턴스 저장

##### List\<E> 인터페이스를 구현하는 컬렉션 클래스들이 갖는 공통적인 특징
1. 인스턴스의 저장 순서를 유지
2. 동일한 인스턴스의 중복 저장을 허용

```
package yoon;

import java.util.ArrayList;
import java.util.List;

public class ArrayListCollection {
    public static void main(String [] args) {
        List<String> list = new ArrayList<>();
        // 컬렉션 인스턴스 생성

        // 컬렉션 인스턴스에 문자열 인스턴스 저장
        list.add("Toy");
        list.add("Boy");
        list.add("Robot");

        // 인스턴스 참조
        for (String s: list)
            System.out.print(s + "\t");
        System.out.println();

        list.remove(0); // 첫번째 인스턴스 삭제
        for (String s: list)
            System.out.print(s + "\t");
        System.out.println();
    }
}
//result
Toy	Boy	Robot	
Boy	Robot	
```

- List\<String> list = new ArrayList<>();에서 List\<E>형으로 참조를 한 이유는 유연성을 제공하기 위해서이다. 위와같이 선언을 하면 new LinkedList<>();로도 선언이 가능하다. 

#### LinkedList\<E> 클래스

- ArrayList<>()와 차이는 생성을 할때, LinkedList<>();가 달라진게 문장변화의 전부이다.

```
package yoon;

import java.util.LinkedList;
import java.util.List;

public class LinkedListCollection {
    public static void main(String [] args) {
        List<String> list = new LinkedList<>();
        list.add("Toy");
        list.add("Box");
        list.add("Robot");

        for (String s: list)
            System.out.print(s + "\t");
        System.out.println();

        list.remove(0);

        for (String s: list)
            System.out.print(s + "\t");
        System.out.println();
    }
}
//result
Toy	Boy	Robot	
Boy	Robot	
```
- LinkedList<>()는 연결리스트가 기반이 된 클래스이다. 연결리스트는 칸칸이 연결된 화물열차를 생각을 하면된다.
- ArrayList<>()와 달리 인스턴스의 저장공간을 미리 확보를 안해도 된다.

### ArrayList\<E> vs LinkedList\<E>

#### ArrayList<>()의 단점
1. 저장공간을 늘리는 과정에서 시간이 많이 필요하다.
2. 인스턴스의 삭제 과정에서 느리다.

#### ArrayList<>()의 장점
1. 저장된 인스턴스의 참조가 빠르다.

#### LinkList<>()의 단점
1. 참조과정이 복잡해서 읽는데 느리다.

#### LinkedList<>()의 장점
1. 저장공간을 늘리기가 쉽다.
2. 저장된 인스턴스를 삭제하기가 쉽다.


### 저장된 인스턴스의 순차적 접근

- Iterator\<T> iterator() : 이 메소드는 반복자를 반환한다.
- E next() : 다음 인스턴스의 참조값을 반환
- boolean hasNext() : next메소드 호출 시 참조 값 반환 가능 여부를 확인
- void remove() : next메소드 호출을 통해 반환했던 인스턴스 삭제

#### 반복자는 next를 호출할 때마다 첫 인스턴스를 시작으로 다음 인스턴스의 참조 값을 차례로 반환한다. 더 이상 반환할 대상이 없을 때, NoSuchElementException 예외를 발생시킨다.

```
package yoon;

import java.util.Iterator;
import java.util.LinkedList;
import java.util.List;

public class IteratorCollection {
    public static void main(String [] args) {
        List<String> list = new LinkedList<>();
        list.add("Toy");
        list.add("Box");
        list.add("Robot");
        list.add("Box");

        Iterator<String> itr = list.iterator(); // 반복자 획득

        while (itr.hasNext())
            System.out.print(itr.next() + "\t");
        System.out.println();

        itr = list.iterator(); // 반복자 다시 획득

        String str;
        while (itr.hasNext()) {
            str = itr.next();
            if(str.equals("Box"))
                itr.remove();
        }

        itr = list.iterator();

        while (itr.hasNext())
            System.out.print(itr.next() + "\t");
        System.out.println();
    }
}
//result
Toy	Box	Robot	Box	
Toy	Robot	
```

### 연결 리스트만 갖는 양방향 반복자

public ListIterator\<E> listIterator() : ListIterator\<E>는 Iterator\<E>를 상속한다.

- E next()
- boolean hasNext()
- void remove()
- E previous() : next메소드와 기능은 같고 방향이 반대
- boolean hasPrevious() : hasNext와 기능은 같고 방향이 반대
- void add(E e) : 인스턴스 추가
- void set(E e) : 인스턴스 변경

```
package yoon;

import java.util.*;

public class ListIteratorCollection {
    public static void main(String [] args) {
        List<String> list = Arrays.asList("Toy", "Box", "Robot", "Box");
        list = new ArrayList<>(list);

        ListIterator<String> litr = list.listIterator(); // 양방향 반복자 획득

        String str;
        while (litr.hasNext()) {
            str = litr.next();
            System.out.print(str + "\t");
            if(str.equals("Toy")) // Toy 만나면 Toy2 저장
                litr.add("Toy2");
        }
        System.out.println();

        while (litr.hasPrevious()) {
            str = litr.previous();
            System.out.print(str + "\t");
            if (str.equals("Robot")) // Robot을 만나면 Robot2를 저장
                litr.add("Robot2");
        }
        System.out.println();

        // 다시 왼쪽에서 오른쪽으로
        for(Iterator<String> itr = list.iterator(); itr.hasNext(); )
            System.out.print(itr.next() + "\t");
        System.out.println();
    }
}
//result
Toy	Box	Robot	Box	
Box	Robot	Robot2	Box	Toy2	Toy	
Toy	Toy2	Box	Robot2	Robot	Box	
```
