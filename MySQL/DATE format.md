## MySQL DATE type

### **DATE 타입**

DATE 타입은 시간을 포함하지 않는 날짜만 사용하는 타입이다.

YYYY-MM-DD 형식으로 입력

ex) 2021-02-04

</br>

### **DATETIME 타입**

DATETIME 타입은 날짜와 시간 모두 포함하는 타입이다.

YYYY-MM-DD HH:MM:SS 형식으로 입력

ex) 2021-02-04 22:30:33

</br>

### **TIME 타입**

TIME 타입은 날짜를 포함하지 않는 시간만 사용하는 타입이다.

HH:MM:SS 형식으로 입력

ex) 22:30:33

</br>

### **TIMESTAMP 타입**

TIMESTAMP 타입은 날짜와 시간 모두 포함하는 타입이다.

YYYY-MM-DD HH:MM:SS 형식으로 입력

ex) 2021-02-04 22:30:33

</br>

### **DATETIME과 TIMESTAMP의 차이**

1. 타입

DATETIME은 문자형

TIMESTAMP는 숫자형

2. 용량

DATETIME은 8byte

TIMESTAMP는 4byte

3. 입력

DATETIME은 값을 입력해줘야 한다.

TIMESTAMP는 값을 입력하지 않으면 자동으로 현재 날짜가 입력된다.

</br>

### **java DATE format 방법**

```java
public String void makeDate() {
        Calendar calendar = Calendar.getInstance();
        calendar.setTime( new Date());
        SimpleDateFormat dateFormat = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        return dateFormat.format(calendar.getTime());
    }
```

SimpleDateFormat을 이용하여 포맷을 할 수 있다.

yyyy-MM-dd HH:mm:ss -> 2021-02-04 22:30:33

yyyy-MM-dd -> 2021-02-04

HH:mm:ss -> 22:30:33
