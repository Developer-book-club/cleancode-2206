# 6장 객체와 자료구조

변수를 비공개 private로 정의하는 이유는 남들이 변수에 의존하지 않게 만들고 싶어서다. 충동이든 변덕이든, 변수 타입이나 구현을 맘대로 바꾸고 싶어서다.  조회get 함수와 설정set 함수를 당연하게 공개public해 비공개 변수를 외부에 노출하고 있다!

## **자료 추상화**

### 목록 **6-1 구체적인 Point 클래스**

`public class Point { 
  public double x; 
  public double y;
}`

### 목록 **6-2 추상적인 Point 클래스**

`public interface Point {
  double getX();
  double getY();
  void setCartesian(double x, double y); 
  double getR();
  double getTheta();
  void setPolar(double r, double theta); 
}`

목록 6-1은 내부 구조를 노출, 좌표값을 읽고 설정하게한다. 

목록 6-2는 구현을 완전히 숨긴다. 그에 반해 일반적으로 변수를 private으로 선언하고, 값마다 get과 set 함수를 제공한다면 이는 결과적으로 내부 구조를 노출하는 구조가 된다. set, get 메서드로 변수를 다룬다고 클래스가 되는 것이 아니라, 추상 인터페이스를 제공해서 자료의 핵심을 조작할 수 있어야 진정한 의미의 클래스다.

## **자료/객체 비대칭**

- 객체는 추상화 뒤로 자료를 숨긴 채 **자료를 다루는 함수**만 공개한다.
- 자료 구조는 **자료를 그대로 공개**하며 별다른 함수는 제공하지 않는다.

두 정의는 본질적으로 상반된다.사소한 차이로 보일지 모르지만 그 차이가 미치는 영향은 굉장하다.

> (자료 구조를 사용하는) 절차적인 코드는 기존 자료 구조를 변경하지 않으면서 새 함수를 추가하기 쉽다. 반면, 객체 지향 코드는 기존 함수를 변경하지 않으면서 새 클래스를 추가하기 쉽다.
> 

반대쪽도 참이다.

> 절차적인 코드는 새로운 자료 구조를 추가하기 어렵다. 그러려면 모든 함수를 고쳐야 한다. 객체 지향 코드는 새로운 함수를 추가하기 어렵다. 그러려면 모든 클래스를 고쳐야 한다.
> 

**객체 지향 코드에서 어려운 변경은 절차적인 코드에서 쉬우며, 절차적인 코드에서 어려운 변경은 객체 지향 코드에서 쉽다!**

상황에 맞게 **클래스 & 객체 지향 기법**을 사용하거나, **절차적인 코드와 자료 구조**를 적절하게 사용하는 것이 좋다.

때로는 단순한 자료 구조와 절차적인 코드가 가장 적합한 상황도 있다.

### **기차 충돌**

다음과 같은 코드를 기차 충돌train wreck이라 부른다.

`final String outputDir = ctxt.getOptions().getScratchDir().getAbsolutePath();`

여러 객체가 이어진 기차처럼 보이기 때문이다. 위 코드는 다음과 같이 나누는 편이 좋다.

`Options opts = ctxt.getOptions();
File scratchDir = opts.getScratchDir();
final String outputDir = scratchDir.getAbsolutePath();`

### **구조체 감추기**

`outputDir` 예제의 경우 좋은 방식이 아니다. 한참 아래로 내려가서 왜 필요한지 찾았더니 이런 코드가 있다.

`String outFile = outputDir + "/" + className.replace('.', '/') + ".class"; 
FileOutputStream fout = new FileOutputStream(outFile); 
BufferedOutputStream bos = new BufferedOutputStream(fout);`

추상화 수준을 뒤섞어 놓아 다소 불편하다. 점, 슬래시, 파일 확장자, File 객체를 부주의하게 마구 뒤섞으면 안 된다. 어찌 되었거나, 위 코드에 따르면 경로를 얻으려는 이유가 임시 파일을 생성하기 위함을 알 수 있다.

그렇다면 ctxt 객체에 임시 파일을 생성하라고 시키면 어떨까?

`BufferedOutputStream bos = ctxt.createScratchFileStream(classFileName);`

객체에게 맡기기에 적당하게 보인다. ctxt는 내부 구조를 드러내지 않으며, 모듈은 자신이 몰라야 하는 여러 객체를 탐색할 필요가 없다. 따라서 디미터 법칙을 위반하지 않는다.

- 객체는 동작을 공개하고 자료를 숨긴다. 그래서 기존 동작을 변경하지 않으면서 새 객체 타입을 추가하기는 쉬운 반면, 기존 객체에 새 동작을 추가하기는 어렵다.
- 자료 구조는 별다른 동작 없이 자료를 노출한다. 그래서 기존 자료 구조에 새 동작을 추가하기는 쉬우나, 기존 함수에 새 자료 구조를 추가하기는 어렵다.
- 새로운 자료 타입을 추가하는 유연성이 필요하면 객체가 더 적합하다. 다른 경우로 새로운 동작을 추가하는 유연성이 필요하면 자료 구조와 절차적인 코드가 더 적합하다.