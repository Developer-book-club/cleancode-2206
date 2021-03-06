# 02장. 의미 있는 이름

## 의도를 분명히 밝혀라
좋은 이름을 지으려면 시간이 걸리지만 좋은 이름으로 절약하는 시간이 훨씬 더 많다.
의도가 드러나는 이름을 사용하면 코드 이해와 변경이 쉬워진다. 
의도가 드러나는 이름을 쓰는것만으로도 코드는 더욱 명확해진다. -> 좋은 이름이 주는 위력!

## 그릇된 정보를 피하라
프로그래머는 코드에 그릇된 단서를 남겨서는 안 된다. 그릇된 단서는 코드의 의미를 흐림.
나름대로 널리 쓰이는 의미가 있는 단어를 다른 의미로 사용해도 안 됨.
서로 흡사한 이름을 사용하지 않도록 주의. 

유사한 개념은 유사한 표기법을 사용. 일관성이 떨어지는 표기법은 그릇된 정보.
l과 1, O과 0 끔찍!

## 의미 있게 구분하라
컴파일러나 인터프리터만 통과하려는 생각으로 코드를 구현하는 프로그래머는 스스로 문제를 일으킴.
연속된 숫자를 덧붙이거나 불용어(noise word)를 추가하는 방식은 적절하지 못함. -> 이름이 달라야한다면 의미도 달라야함.

연속적인 숫자를 덧붙인 이름 (a1,a2 ... aN)은 의도적인 이름과 정반대.
그릇된 정보를 제공하는 이름도 아니고, 아무런 정보를 제공하지 못하는 이름. 저자 의도가 전혀 드러나지 않음.

productInfo 나 productData 는 개념을 구분하지 않은 채 이름만 달리한 경우.
info나 data는 a,an,the와 마찬가지로 의미가 불분명한 불용어.

읽는 사람이 차이를 알도록 이름을 지어라.

## 발음하기 쉬운 이름을 사용하라

## 검색하기 쉬운 이름을 사용하라
문자 하나를 사용하는 이름과 상수는 텍스트 코드에서 쉽게 눈에 띄지 않는다는 문제점이 있다.
이름을 의미있게 지으면 함수가 길어진다. 

## 인코딩을 피하라 
인코딩한 이름은 거의가 발음하기 어려우며 오타가 생기기도 쉽다. 

## 자신의 기억력을 자랑하지 마라
문자 하나만 사용하는 변수 이름은 문제가 있다. 루프에서 반복 횟수를 세는 변수 i,j,k는 괜찮다. 그 외는 적절하지 못함.
똑똑한 프로그래머와 전문가 프로그래머 사이의 차이점은 전문가 프로그래머는 명료함이 최고라는 사실을 이해함.
그리고 자신의 능력을 좋은 방향으로 사용해 남들이 이해하는 코드를 내놓음.

## 클래스 이름
클래스 이름, 객체 이름은 명사나 명사구가 적합. 동사는 사용하지 않는다.

## 메서드 이름
동사, 동사구가 적합 
생성자를 중복정의할 때는 정적 팩토리 메서드를 사용. 

## 기발한 이름은 피하라
이름이 너무 기발하면 저자와 유머 감각이 비슷한 사람만, 그리고 농담을 기억하는 동안만, 이름을 기억.
재미난 이름보다 명료한 이름! 의도를 분명하고 솔직하게 표현하라.

## 한 개념에 한 단어를 사용하라
동일 코드 기반에 controller, manager, driver를 섞어 쓰면 혼란스럽다. 
이름이 다르면 독자는 당연히 클래스도 다르고 타입도 다르리라 생각한다.

## 말장난을 하지 마라
한 단어를 두 가지 목적으로 사용하지 마라. 다른 개념에 같은 단어를 사용한다면 그것은 말장난!
프로그래머는 코드를 최대한 이해하기 쉽게 짜야한다. 집중적인 탐구가 필요한 코드가 아니라 대충 훑어봐도 이해할 코드 작성이 목표.

## 해법 영역에서 가져온 이름을 사용하라
코드를 읽은 사람도 프로그래머라는 사실을 명심한다.
모든 이름을 문제 영역(domain)에서 가져오는 정책은 현명하지 못함. 

## 문제 영역에서 가져온 이름을 사용하라
적절한 '프로그래머 용어'가 없다면 문제 영역에서 이름을 가져온다. 
그럼 코드를 보수하는 프로그래머가 분야 전문가에 의미를 물어 파악할 수 있다.

## 의미 있는 맥락을 추가하라
클래스, 함수, 이름공간에 넣어 맥락을 부여. 모든 방법이 실패하면 마지막으로 접두어를 붙임.

## 불필요한 맥락을 없애라
일반적으로는 짧은 이름이 긴 이름보다 좋다. 단, 의미가 분명한 경우에 한해서.
이름에 불필요한 맥락을 추가하지 않도록 주의.