# .siblings
* 선택한 요소를 제외한 형제 요소를 모두 찾는다.
    * $("선택").siblings();
```javascript
$(".select1").siblings()
```
* 선택한 요소를 제외한 형제 중에서 객체를 찾는다.
    * $("선택").siblings("객체");
```javascript
$(".select1").siblings(".select2")
```

# 이벤트 다중 선택
* 이벤트를 여러개 걸어줄 때 쉼표로 구분해서 넣어주면 한꺼번에 이벤트가 걸린다.
* 비동기 처리시 documnet에 on으로 클릭 이벤트를 해주면 비동기 처리시 나중에 생성되는 셀렉터들도 이벤트 처리가 된다.
```html
<body>
    <div id="aa">aa</div>
    <div id="bb">bb</div>
    <div name="cc">cc</div>
</body>
<script>
   $(document).on("click", "#aa, #bb, [name=cc]", function(){
      console.log("aa and bb") 
   })
</script>
```
```javascript

```
