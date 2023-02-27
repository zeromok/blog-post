# Enum 이란?

Java에서 enum은 상수를 나타내는 특별한 클래스라고 하고, 일반적으로 한정된 상수 집합을 나타내는 데 사용한다.

## Enum의 특징

> Java에서 enum(열거형)은 특정 유형의 상수 값을 정의할 수 있는 데이터 형식이다.  
이러한 상수 값은 컴파일러가 강력하게 검사하기 때문에 안정적인 코드를 작성하는 데 도움이 된다.


- 상수 집합:  
    enum은 상수의 집합을 나타냅니다. 이러한 상수는 코드에서 정의된 순서대로 정렬됩니다.

- 클래스 형태:  
    enum은 클래스와 마찬가지로 정의됩니다. 이는 상수 외에도 메서드, 생성자, 변수 및 상수를 포함할 수 있다는 것을 의미합니다.

- 싱글톤 패턴:  
    enum은 싱글톤 패턴을 구현하기 위해 사용될 수 있습니다. 이러한 경우 enum 상수 중 하나가 전체 어플리케이션에서 단 하나의 인스턴스로 취급됩니다.

- 안전성:  
    enum은 안전성을 제공합니다. enum의 모든 인스턴스는 컴파일 타임에 알려져 있기 때문에 오타나 잘못된 상수 값의 입력을 방지할 수 있습니다.

- switch 문에서 사용 가능:  
    enum은 switch 문에서 사용할 수 있습니다. 이는 코드를 더 읽기 쉽게 만듭니다.

- 사용자 정의 메서드:  
    enum은 사용자 정의 메서드를 가질 수 있습니다. 이는 특정 enum 상수에서 특정 동작을 수행해야 할 때 사용됩니다.

## Enum 사용법

- Enum은 클래스이므로, 클래스와 동일하게 생성할 수 있다.  
하지만 __Enum은 생성자를 가질 수 없다.__

```
public enum Weekday {  
    MONDAY,  
    TUESDAY,  
    WEDNESDAY,  
    THURSDAY,  
    FRIDAY,  
    SATURDAY,  
    SUNDAY  
}  
```

위 코드에서 Weekday라는 이름의 Enum 클래스를 생성하고, 해당 클래스의 상수로서 MONDAY, TUESDAY 등을 선언했다.


- ### Enum 선언하기
    - Enum 값은 해당 클래스의 상수로서 사용할 수 있다.  
    일반적으로 switch문이나 if-else문에서 많이 사용한다.
    ```
    public static void main(String[] args) {
        Weekday today = Weekday.MONDAY;

        switch (today) {
            case MONDAY:
                System.out.println("오늘은 월요일입니다.");
                break;
            case TUESDAY:
                System.out.println("오늘은 화요일입니다.");
                break;
            case WEDNESDAY:
                System.out.println("오늘은 수요일입니다.");
                break;
            case THURSDAY:
                System.out.println("오늘은 목요일입니다.");
                break;
            case FRIDAY:
                System.out.println("오늘은 금요일입니다.");
                break;
            case SATURDAY:
                System.out.println("오늘은 토요일입니다.");
                break;
            case SUNDAY:
                System.out.println("오늘은 일요일입니다.");
                break;
        }
    }

    ```

    위 코드에서는 Weekday 클래스의 MONDAY 값을 today 변수에 할당하고, switch문을 통해 해당 값에 따라 적절한 문구를 출력한다.


- ### Enum 메서드 사용하기
    Enum 메서드를 활용하면 Enum 상수에 대한 작업을 더 쉽게 수행할 수있다.

    ```
    public enum Day {
        SUNDAY, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY;

        public boolean isWeekend() {
            return this == SATURDAY || this == SUNDAY;
        }

        public String getShortName() {
            switch (this) {
                case MONDAY:
                    return "Mon";
                case TUESDAY:
                    return "Tue";
                case WEDNESDAY:
                    return "Wed";
                case THURSDAY:
                    return "Thu";
                case FRIDAY:
                    return "Fri";
                case SATURDAY:
                    return "Sat";
                case SUNDAY:
                    return "Sun";
                default:
                    return "";
            }
        }
    }

    ```
    위 Enum은 일주일의 요일을 나타내는 상수를 가지고있다.  

    아래의 메서드를 추가해 활용해보았다.  
    `isWeekend()` : 주말인지 아닌지?  
    `getShortName()` : SUNDAY == SUN 처럼 줄인 문자열을 반환


- ### Enum 활용 
    Enum은 코드의 가독성과 유지보수를 높이는 데에 큰 도움을 준다.  
    예를 들어, 상수를 사용할 경우, 오타 등의 실수로 인해 값이 잘못될 가능성이 있지만, Enum을 사용하면 이러한 문제를 방지할 수 있다.  
    또한 Enum을 사용하면, 해당 값의 이름과 기능이 연결된 메서드를 쉽게 구현할 수 있으므로, 코드의 가독성이 높아진다.  
    따라서, Enum은 Java에서 매우 유용한 기능 중 하나이지만, Enum 값이 많은 경우, 성능 이슈가 발생할 수 있으므로, 이를 고려해 잘 사용해보자


## Enum의 장단점

- ### 장점
    - 가독성이 좋아진다.
    - 안정성이 높아진다.
    - 코드 유지보수가 용이하다.
    - 코드의 안정성을 보장한다.

- ### 단점
    - Enum의 크기가 커질 수 있다.
    - 다른 클래스와 함께 사용하기 어렵다. 왜? Enum은 자바에서 독립적인 데이터 타입이기 때문에...

## Enum 네이밍 규칙

- ### 클래스명 규칙
    클래스 명명 규칙과 똑같이 첫번째 문자는 대문자로 시작하면 된다.

- ### 상수 값 규칙
    - 대문자로 작성  
    - 각 단어는 언더바로 구분한다.(snake case)
    - 숫자로 시작할 수없다.
    - 고유한 이름을 가져야 한다.
    - Enum 클래스 내부에서 정의된 상수들은 해당 Enum 클래스의 인스턴스들 중에서만 사용 가능하다.

## Enum과 인터페이스의 결합
Java Enum과 인터페이스는 함께 사용될 때 매우 유용하다.  
아래의 예와같이 애플리케이션이 다양한 유형의 도형을 다룬다고 가정해보자.  
이때, 각 도형은 특정 인터페이스를 구현해야한다.  
이 경우, Java Enum과 인터페이스를 결합하여 아래와 같이 구현할 수 있다.

```
public interface Shape {
    double getArea();
}

public enum ShapeType implements Shape {
    CIRCLE {
        @Override
        public double getArea() {
            return Math.PI * Math.pow(radius, 2);
        }
    },
    RECTANGLE {
        @Override
        public double getArea() {
            return length * width;
        }
    },
    TRIANGLE {
        @Override
        public double getArea() {
            return 0.5 * base * height;
        }
    };

    // 각 도형의 필드
    private double radius;
    private double length;
    private double width;
    private double base;
    private double height;

    // 각 도형의 생성자 및 getter/setter 메소드
    // ...

}
```
위 코드에서는 Shape 인터페이스를 구현하는 ShapeType 열거형 상수를 정의했다.  
각 상수는 getArea() 메소드를 구현하고, 필요한 필드와 메소드를 설정해줬다.  
이렇게 구현된 Enum과 인터페이스를 함께 사용하면, 아래와 같이 사용할 수 있다.

```
Shape shape = ShapeType.CIRCLE;
double area = shape.getArea();
```
위와 같이 ShapeType 열거형 상수를 이용해 Shape 인터페이스를 구현한 객체를 생성하고,  
이 객체의 getArea() 메소드를 호출하여 도형의 넓이를 구할 수있다.

## Enum vs 상수
- ### Constant(상수)
    : 변하지 않는 값을 나타내며, 일반적으로 `final` 키워드로 선언된다.
- ### Enum(열거형)
    : 상수의 값을 정의하고 이를 나열한것 -> 상수 값의 범위를 명확하게 정할 수 있다.

## Note
- 2023-02-27 첫발행  
    > 프로젝트를 하며 더욱 더 깊게 알게되고 새로워보여 공부하고 정리해보았다.