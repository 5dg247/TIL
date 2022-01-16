# Promise 함수

* 자바스크립트 특성상 **비동기식 처리**때문에 나오게 된 함수라고 봐도 무방하다.
* **비동기식 처리**때문에 순서대로 함수를 적어도 결과 값이 없다고 나올 떄가 많은데 이를 해결 하기 위해 promise 함수가 생겼다.

```javascript
function test(){
    return new promise(function(resolve, reject){
        resolve(성공),
        reject(실패);
    });

test().then(function(respon){
    console.log(respon);
}).catch(function(error){
    console.log(error);
})
```
* test()함수를 실행해서 값이 성공적으로 온다면 resolve()함수를 불러오고 그게 아니라면 reject()함수를 실행한다.
* 그렇게 불려온 성공한 resolve()함수의 값은 promise의 then()함수로 이어지고 거기에 resolve의 '성공'값이 respon으로 들어가게 된다. 그 외의 에러 값들은 reject()함수의 '실패'값이 catch의 error로 들어가게 된다.

```javascript
function test(){
    return new promise(function(resolve, reject){
        resolve(1);
    });
}


test().then(function(data1){
    console.log(data1); //1
    return data1 + 10;
}).then(function(data2){
    console.log(data2);//11
    return data2 + 10;
}).then(function(data3){
    console.log(data3);//21
});
```
* 이걸 이용해서 promise chaining을 쓸 수 있다. 프로미스의 then의 결과값은 promise 객체 값이기 떄문에 계속해서 then() 함수를 이용할 수 있다. then()함수의 연속적인 호출은 자바스크립트의 특성인 비동기식 처리에 아주 유용하게 써먹을 수 있다.