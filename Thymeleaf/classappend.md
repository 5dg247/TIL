# th:classappend
* 보통 동적 클래스를 추가할때 if와 함께 쓰인다.
```javascript
<a href="" class="baseclass" th:classappend="${isAdmin} ? adminclass : userclass"></a>
isAdmin 이 트루면
<a href="" class="baseclass adminclass"></a>
```
* if문을 이용해서 `보통 삼항연산자를 쓴다 - (if문) ? true : else` 기존에 있던 baseclass에 다른 클래스를 더해준다. 이걸 이용해서 css의 동적 스타일 지정이 가능하다. 보통 `on`이나 `active` 같은걸 추가해서 사용한다.