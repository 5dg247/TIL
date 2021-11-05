# Test케이스 작성
* 개발한 기능을 실행해서 테스트 할 때 자바의 main 메서드를 통해서 실행하거나, 웹 애플리케이션의 컨트롤러를 통해서 해당 기능을 실행하면 오래 걸리고 반복 실행하기 어렵다. 여러 테스트들을 한꺼번에 하기 어렵다. 이를 해결하기 위해 자바는 JUnit이라는 프레임워크로 테스트를 실행해서 이러한 문제를 해결한다.

* 보통 src/test 아래에 똑같이 패키지를 만들어서 실험을 한다.
* 보통 실험할 클래스 뒤에 Test를 붙여서 테스트 할 클래스를 만든다.  
실험할 클래스 : MemberRepository  
테스트 할 클래스 : MemberRepositoryTest

* 메인 메소드처럼 동작하게 하기 위해서 메소드 작성 후에 어노텐션인 @Test를 
* 테스트 클래스에서 테스트 할 클래스를 생성한다.
* 생성해둔 테스트 할 클래스를 이용하여 테스트 동작을 할 메소드를 만들고 실행한다.

# assertThat()
```Java
Assertions.assertThat(actual).isEqualTo(expected);
```
* Test를 통해서 파라메타 값들을 비교할 때 쓰는 메소드이다. 다른 비교방법들은 무수히 많지만 요즘 추세가 asserThat을 쓰는데 이유는 테스트 메소드를 동작 했을 때 `actual`(실제 값)과 `expected`(예상되는 값, 비교되는 값) 값 둘 다 출력이 돼서 비교를 더 명확하게 할 수 있다. 
* 인텔리제이에서는 Assertions에 커서를 대고서 `Alt + Enter` 를 쓰면 Assertions가 impoert static이 되어서 asserThat만 써도 이용가능하게 바뀐다.
* 테스트를 먼저하고 그 다음에 개발을 이어나가는 것을 테스트 주도 개발(TDD - Test Driven Development)이라한다.