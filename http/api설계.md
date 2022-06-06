# HTTP API 설계
## POST 기반 등록 API 설계 (회원관리시스템)
* 회원 목록 - /members - GET
* 회원 등록 - /members - POST
* 회원 조회 - /members/{id} - GET
* 회원 수정 - /members/{id} - PATCH, PUT, POST
    * 회원 수정을 할때는 개념적으론 PATCH가 좋다. 하지만 PUT을 쓸 수도 있다. 그럼에도 잘 쓰지 않는 이유는 PUT을 쓰려면 모든 데이터를 다시 보내야 하는데 그 중 하나라도 빠지면 빠진 데이터는 새로 수정이 되는 것이 아니라 사라지게 된다. 이것도 저것도 애매한 상황이라면 POST를 쓰는 것이 맞다.
* 회원 삭제 - /members/{id} - DELETE
* **URI로 리로스를 식별하는 것은 리소스 그 자체를 식별해야지 다른 것을 식별하면 안된다.**
* EX - 회원관리 라면 회원이 리소스기 때문에 members 라고 URI를 작성한다.

## POST - 신규 자원 등록 특징
* 클라이언트는 등록될 리소스 URI를 모른다.
    * 회원등록 /members -> POST
    * POST /members
* 서버가 새로 등록된 리소스 URI를 생성해준다.
    * HTTP/1.1 201 Created<br>Location : **/members/100**
* 컬렉션(Collection)
    * 서버과 관리하는 리소스 디렉토리
    * 서버가 리소스의 URI를 생성하고 관리를 컬랙션이라 한다.
    * 여기서 컬랙션은 /members 이다.
* 거의 대부분 POST 기반의 컬랙션을 사용한다.

## PUT 기반 등록 API 설계 (파일관리시스템)
* 파일 목록 /files -> GET
* 파일 조회 /files/{filename} -> GET
* 파일 등록 /files/{filename} -> PUT
* 파일 삭제 /files/{filename} -> DELETE 
* 파일 대량 등록 /files -> POST

## PUT - 신규 자원 등록 특징
* 클라이언트가 리소스 URI를 알고 있어야 한다.
    * 파일 등록 /files/{filename} -> PUT
    * PUT /files/star.jpg
* 클라이언트가 직접 리소스의 URI를 지정한다.
* 스토어(Store)
    * 이런 스타일로 관리를 하는 것을 스토어라 한다.
    * 클라이언트가 관리하는 리소스 저장소
    * 클라이언트가 리소스의 URI를 알고 관리
    * 여기서 스토어는 /files

## HTML FORM 사용
* HTML FORM은 GET, POST만 사용
* AJAX 같은 기술을 사용해서 해결 가능 -> 회원 API 참고
* 순수 HTML, HTML FORM 설명들
* GET, POST 만 사용하므로 제약들이 있다.

## HTML FORM 설계
* 회원 목록 /members -> GET
* 회원 등록 폼 /members/new -> GET
* 회원 등록 /members/new, /members -> POST
    * 똑같이 등록할 수 있는 폼을 불러오는 것과 등록 URI를 같이 하는 것이 좋다. 서버에 등록을 던졌는데 서버에 문제가 생겨서 다시 돌아와야 되는 상황이라면 URI가 같은 것이 좋다. 다시 되돌아와야 하기 떄문이다.
* 회원 조회 /members/{id} -> GET
* 회원 수정 폼 /members/{id}/edit -> GET
* 회원 수정 /members/{id}/edit, /members/{id} -> POST
    * 등록 폼과 등록과 마찬가지로 FORM 자체를 불러오는 것은 DB자체에 수정을 하는 것이 아니기 떄문에 같에 해도 무관하다.
* 회원 삭제 /members/{id}/delete -> POST
    * HTML FORM은 GET과 POST만 사용할 수 있기 떄문에 어쩔 수 없이 URI에 행동을 나타내는 delete를 쓸 수 밖에 없다.

### 컨트롤 URI를 써야 한다.
* GET POST만 지원 하므로 제약이 있다.
* 이런 제약을 해결하기 위해서 행동(동사)로 된 리소스 경로를 사용한다
* POST의 /new /edit /delete 같은 것들이 컨트롤 URI
* HTTP 메서드로 해결하기 애매한 경우에 사용한다.(HTTP API) 포함
    * 이상적으로는 HTTP 메서드로 해결하면 좋겠지만 실무에서는 다양한 경우가 있기 때문에 컨트롤 URI로 해결한다.
    * 최대한 리소스 개념을 가지고 URI를 설계를 하고 그 다음에 컨트롤 URI를 쓴다.

## 참고하면 좋은 URI 개념
* 문서(document)
    * 단일 개념(파일 하나, 객체 인스턴스, 데이터베이스 row)
    * 단 하나의 파일같은 것을 지칭할 때, 단 하나를 나타낼 떄
    * 예) /members/100, /files/star.jpg
* 컬렉션(collection)
    * 서버가 관리하는 리소스 디렉토리
    * 서버가 리소스의 URI를 생성하고 관리
    * 예) /members
* 스토어(store)
    * 클라이언트가 관리하는 자원 저장소
    * 클라이언트가 리소스의 URI를 알고 관리
    * 예) /files
* 컨트롤러(controller), 컨트롤 URI
    * 문서, 컬렉션, 스토어로 해결하기 어려워 추가 프로세스가 필요할 때
    * 동사, 행동을 직접 사용한다.
    * 실무는 복잡한 환경에 놓여있기 때문에 HTTP 메소드로는 해결 안되는 것들이 많다.
    * 예) /members/{id}/delete
    * **최대한 리소스에 대한 생각을 먼저 잡아두고 URI 설계를 해야한다.** 그 다음에 컨트롤 URI를 생각해야 좋은 설계라고 할 수 있다.
