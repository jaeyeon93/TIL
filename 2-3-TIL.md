#### Date

- Date는 지역화에 대한 부분이 고려안됬다. 이 부분에 대한 보완으로 Calender가 있다. 그래므로 대부분의 메소드들이 Deprecated(사용중단)이 되어있다.

```
package javautil;

import java.text.SimpleDateFormat;
import java.util.Date;

public class DateExam {
    public static void main(String [] args){
        Date date = new Date();
        System.out.println(date.toString());

        SimpleDateFormat ft = new SimpleDateFormat("yyyy.MM.dd 'at' hh:mm:ss a zzz");

        System.out.println(ft.format(date));

        System.out.println(date.getTime());
        
    }
}
// result
Sat Feb 03 18:30:53 KST 2018
2018.02.03 at 06:30:53 PM KST
1517650253916

```
- yyyy는 년, MM은 월, dd는 일을 표시한다.
- hh는 시간, mm은 분, ss는 초를 표현하며, a는 오전/오후, zzz는 타임존을 나타낸다.

#### Calendar

- Calendar는 추상클래스이다. 그러므로 인스턴스를 생성하려면, 클래스메소드 getInstance()를 사용해야한다.

![](/Users/jaeyeonkim/Desktop/calender.png)

```
package javautil;

import java.util.Calendar;

public class CalendarExam {
    public static void main(String [] args){
        Calendar cal = Calendar.getInstance();

        System.out.println(cal.get(Calendar.YEAR));
        System.out.println(cal.get(Calendar.MONTH) + 1);
        // 월은 0부터 시작을 한다.
        System.out.println(cal.get(Calendar.DATE));

        System.out.println(cal.get(Calendar.HOUR));
        System.out.println(cal.get(Calendar.HOUR_OF_DAY));
        System.out.println(cal.get(Calendar.MINUTE));.
        cal.add(Calendar.HOUR, 5);
        //현재 칼랜더에 시간을 5시간 더하는 방법. 5를 -5로 수정하면 5시가 전을 구할 수 있게 됩니다.
    }
}
//result
2018
2
3
6
18
56
```

- HOUR_OF_DAY는 24시간형태이다.


#### java.time패키지

```
package javautil;

import java.time.LocalDate;
import java.time.LocalDateTime;
import java.time.LocalTime;
import java.time.Month;

public class TimeExam {
    public static void main(String [] args){
        LocalDateTime timePoint = LocalDateTime.now();
        System.out.println(timePoint);

        LocalDate ld1 = LocalDate.of(2012, Month.DECEMBER, 12);
        System.out.println(ld1);

        LocalTime lt1 = LocalTime.of(17, 18);
        System.out.println(lt1);
        LocalTime lt2 = LocalTime.parse("10:15:30");

        LocalDate theDate = timePoint.toLocalDate();
        System.out.println(theDate);
        Month month = timePoint.getMonth();
        System.out.println(timePoint.getMonth());
        System.out.println(month.getValue());
    }
}
```
