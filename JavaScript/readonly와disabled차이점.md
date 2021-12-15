# readonly와 disabled 차이점
* readonly와 disabled는 수정할 수 없게 만드는 점에서 같다. 단, readonly가 붙어있는 테그는 name값으로 호출될 때 값이 가지만 disabled는 가지 않는다.
* 예를 들어 타입이 text나 texarea같은 경우는 readonly가 먹히지만 radio버튼은 먹히지 않는다. 그래서 나온 해결책은 onclick="return false;"이다
```javascript
<input type="radio" name="test" value="0" onclick="return false;"/>
```
* 이렇게 걸어두면 값이 와도 수정하지 못하면서 다시 값을 보낼 수 있다.