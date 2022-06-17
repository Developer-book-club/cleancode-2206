# 2장 **의미있는 이름**

## 분명한 의도

존재 이유, 수행 기능, 사용 방법이 드러나야한다.

- 나쁜예시
    - int d; // elapsed time in days
- 좋은예시
    - int elapsedTimeInDays;
    - int daysSinceCreation;
    - int fileAgeInDays;

- 나쁜예시

```
public List<int[]> getThem() {
    List<int[]> list1 = new ArrayList<int[]>();
    for (int[] x: theList)
    if (x[0] == 4)
        list1.add(x);
    return list1;
}
```

- 공백과 들여쓰기는 적당하고, 변수와 상수의 개수도 많지 않은 편입니다.
    - 그러나 코드 맥락이 코드 자체에 드러나지 않습니다.
        1. `theList`에 무엇이 들어있는가
        2. 0번째 값이 어째서 중요한가
        3. 값 4는 무슨 의미인가
        4. 반환하는 리스트를 어떻게 사용하는가
    
- 좋은 예시

```
public List<int[]> getFlaggedCells() {
    List<int[]> flaggedCells = new ArrayList<int[]>();
    for (int[] cell: gameBoard)
        if (cell.isFlagged())
            flaggedCells.add(cell);
    return flaggedCells;
}
```

### **그릇된 정보를 피하라**

- 중의적/비슷한 명명에 주의하자.
- 개발자에게는 특수한 의미를 가지는 단어(List 등)는 실제 컨테이너가 List가 아닌 이상 accountList와 같이 변수명에 붙이지 말자. 차라리 accountGroup, bunchOfAccounts, accounts등으로 명명하자

### **의미 있게 구분하라**

- 말이 안되는 단어, “a1, a2, …”과 같이 숫자로 구분하는 경우 주의
- 클래스 이름에 Info, Data와 같은 불용어를 붙이지 말자. 정확한 개념 구분이 되지 않음
- 예시
    - `Name` VS `NameString`
    - `getActiveAccount()` VS `getActiveAccounts()` VS `getActiveAccountInfo()` (이들이 혼재할 경우 서로의 역할을 정확히 구분하기 어렵다.)
    - `money` VS `moneyAmount`
    - `message` VS `theMessage`
    

### 발음하기 쉬운 이름

- 나쁜예시

```
class DtaRcrd102 {
    private Date genymdhms;
    private Date modymdhms;
    private final String pszqint = "102";
}
```

- 좋은예시

```
class Customer {
    private Date generationTimestamp;
    private Date modificationTimestamp;
    private final String recordId = "102";
}
```

### **검색하기 쉬운 이름을 사용하라**

- 상수는 static final과 같이 정의해 쓰자.
- 변수 이름의 길이는 변수의 범위에 비례해서 길어진다.

### **인코딩을 피하라**

**변수에 부가 정보를 덧붙여 표기하는 것을 말한다**

- 헝가리안 표기법
    - 변수명에 해당 변수의 타입(String, Int 등)을 적지 말자
- 멤버 변수 접두어
    - 멤버 변수 접두어를 붙이지 말자(m_)
    - this 사용하자
- 인터페이스 클래스와 구현클래스
    - 인터페이스 클래스와 구현 클래스를 나눠야 한다면 **구현 클래스**의 이름을 인코딩하자.
    - `IShapeFactory`와 `ShapeFactory`처럼 인터페이스에는 `I`접두어를 붙이기도 하는데, 이는 주의를 흐트리고 과도한 정보를 제공할 수 있습니다.
    - 구현 클래스에 인코딩을 해서 `ShapeFactoryImp` 등으로 사용하는 편이 좋습니다.
    

### **자신의 기억력을 자랑하지 마라**

- 루프 반복횟수 변수 i,j,k는 괜찮다.
- 한번 더 생각해 변환해야 할만한 변수명을 쓰지 말라.
- 똑똑한 프로그래머와 전문가 프로그래머의 차이는 "명료함".

### **클래스 이름**

- 명사 혹은 명사구(Customer, WikiPage, Account, AddressParser)
- Manager, Processor, Data, Info와 같은 단어는 피하자
- 동사는 사용하지 않는다.

### **메서드 이름**

- 동사 혹은 동사구(postPayment, deletePayment, deletePage, save 등)
- 접근자, 변경자, 조건자는 get, set, is로 시작하자. (추가: should, has 등도 가능)
- 생성자를 오버로드할 경우 정적 팩토리 메서드를 사용하고 해당 생성자를 private으로 선언한다.

`// 첫번째 보다 두 번째 방법이 더 좋다.  
Complex fulcrumPoint = new Complex(23.0);  
Complex fulcrumPoint = Complex.FromRealNumber(23.0);`

### **기발한 이름은 피하라**

- 재미있는 이름 (X) 명료한 이름(O)
    - HolyHandGrenade → DeleteItems
    - whack() → kill()

### **한 개념에 한 단어를 사용하라**

- fetch, retrieve, get
- controller, manager, driver

### **말장난을 하지 마라**

- 한 단어를 두 가지 목적으로 사용하지 말자. 아래와 같은 경우에는 ii를 append 혹은 insert로 바꾸는게 옳겠다.

`public static String add(String message, String messageToAppend)  
public List<Element> add(Element element)`

### **해법 영역(Solution Domain) 용어를 사용하자**

- 개발자라면 당연히 알고 있을 `JobQueue`, `AccountVisitor(Visitor pattern)`등을 사용하지 않을 이유는 없다. 전산용어, 알고리즘 이름, 패턴 이름, 수학 용어 등은 사용하자.

### **문제 영역(Problem Domain) 용어를 사용하자**

- 적절한 프로그래머 용어(위 13)가 없거나 문제영역과 관련이 깊은 용어의 경우 문제 영역 용어를 사용하자.

### **의미 있는 맥락을 추가하라**

- 클래스, 함수, namespace등으로 감싸서 맥락(Context)을 표현하라
- 그래도 불분명하다면 접두어를 사용하자.

### **불필요한 맥락을 없애라**

- `Gas Station Delux` 이라는 어플리케이션을 작성한다고 해서 클래스 이름의 앞에 GSD를 붙이지는 말자. 위 a처럼 접두어를 붙이는 것은 모듈의 재사용 관점에서도 좋지 못하다. 재사용하려면 이름을 바꿔야 한다.(eg, `GSDAccountAddress` 대신 `Address`라고만 해도 충분하다.)