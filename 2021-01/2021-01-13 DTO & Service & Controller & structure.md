# DTO (Data Transfer Object)란?

---

1. dto package
    - 계층간 데이터 교환을 위한 객체이다
        - DB에서 데이터를 얻어 Service나 Controller등으로 보낸 때 사용하는 객체
        - DB의 데이터가 Presentation Logic Tier로 넘어오게 될 때는 DTO의 모습으로 바껴서 오고 가는 것이다
        - 로직을 갖고 있지 않는 순수한 데이터 객체이며, getter/setter 메서드만을 갖는다
        - DB에서 꺼낸 값을 임의로 변경할 필요가 없기 때문에 DTO클래스에는 setter가 없다 (생성자에서 값을 할당)
    - Request와 Response용 DTO는 View를 위한 클래스
        - 자주 변경이 필요한 클래스
        - Presentation Model
        - `toEntity()`메서드를 통해서 DTO에서 필요한 부분을 이용하여 Entity로 만든다
        - Controller Layer에서 Response DTO 형태로 클라에 전달한다
    - VO (Value Object) 와 DTO
        - VO는 DTO와 동일한 개념이지만 readOnly속성을 가진다
        - VO는 특정한 비즈니스 값을 담는 객체이고, DTO는 Layer간의 통신 용도로 오가는 객체이다

# service

---

- 기능
    - `@Autowired Repository`를 통해 repository의 method이용
    - 적절한 Business Logic을 처리한다
    - DAO로 DB에 접근하고 DTO로 데이터를 전달받은 다음, 비지늬스 로직을 처리해 적절한 데이터를 반환함

# Controller (WEB)

---

- 기능
    - 해당 요청 url에 따라 적절한 view와 mapping처리
    - `@Autowired Service`를 통해 service의 method를 이용
    - 적절한 ResponseEntity(DTO)를 body에 담아 Client에 반환
- `@Controller`
    - API와 view를 동시에 사용하는 경우에 사용
    - 대신 API서비스로 사용하는 경우에는 `@ResponseBody`를 사용하여 객체를 반환한다
    - view를 return하는 것이 주 목적이다
- `@RestController`
    - view가 필요없는 API만 지원하는 서비스에서 사용
    - `@RequestMapping`메서드가 기본적으로 `@ResponseBody`의미를 가정한다
    - data  (`json`, `xml`등) return이 주목적: **return ResponseEntity**
    - `@RestController` = `@Controller` + `@ResponseBody`

# 전체 구조 (Package 기준)

---

![INSERT](../public/image/Spring/spring-package-flow.png)

1. Entity Class
    - 테이블과 링크될 클래스이다
2. Repository (DAO)
    - 실제로 DB에 접근하는 객체로 서버와 DB를 연결하는 고리의 역할이다
    - SQL을 사용하여 DB에 접근하며, 적절한 CRUD API를 제공하는 역할을 한다
3. service
    - `Repository`에서 DB에 접근하여  DTO로 데이터를 전달받은 다음 비즈니스 로직을 처리해 적절한 데이터로 가공하여 반환하는 역할이다
4. Controller
    - 요청 url에 따라 적절한 view와 mapping처리를 해준다
    - `service`의 method를 이용하여 적절한 DTO를 body에 담아 Client에 반환한다