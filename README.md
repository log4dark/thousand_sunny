# Spring & Spring Boot
Drop in Spring & Spring Boot  

## 스프링 프레임워크 란
- 스프링  
- 스프링 부트  
- 전자정부 프레임워크  


## IoC/DI (예제)
... 

## AOP  
...  

## PSA  
...  

## 스프링 필수 어노테이션(Annotation)
요약~~~  
+ @Component
  + @Controller, @RestController, @Service, @Configuration, @Data??? (DB 연동)  
+ @Autowired, @Resource  
...  

## MVC & RESTful Controller
...  

###  @Controller (Spring MVC Controller)  
#### Controller - View  
전통적인 Spring MVC의 컨트롤러인 @Controller는 주로 View를 반환하기 위해 사용.   
#### Controller - Data    
Spring MVC Controller 에서 (JSON) Data를 반환해야 하는 경우, @ResponseBody 어노테이션 사용. 

```java
@Controller 
public class StudentController {
    @PostMapping(value = "/xxx",
            produces = MediaType.APPLICATION_JSON_VALUE)
    public @ResponseBody List<Student> students() {
        List<Student> list = ...; 
        return list;
    }
}
```
메소드의 리턴타입 앞에 **@ReponseBody** 어노테이션을 설정하면,  
리턴 객체(예:list)를 HTTP 요청 메시지의 Content-Type 기반으로 HTTP response body를 생성하여 리턴.  

### @RestController (Spring RESTful Controller)
@Controller + @ResponseBody  

```java
@RestController
public class StudentController { 
    @PostMapping(value = "/xxx",
            produces = MediaType.APPLICATION_JSON_VALUE)
    public @ResponseBody List<Student> students() {
	public List<Student> students() { 
        List<Student> list = ...; 
        return list; 
    }
}
```

@ResponseBody 생략 해도, 객체를 (JSON)Data로 변환하여 리턴.  

```java
public String update(@RequestBody Student student) { ... }
```

@RequestBody 어노테이션 설정 시,  
Content-Type 헤더 기반으로 HTTP request body를 도메인 객체(예:student)로 변환.

### @ResponseEntity  
XxxController의 리턴타입으로 @ResponseEntity 설정 시,  
- 전체 HTTP 응답을 나타낸다.
- 상태 코드, 헤더 및 body를 지정할 수 있다.
- HTTP Response에서 보내려는 정보를 전달하는 여러 생성자가 제공된다.  

```java
public ResponseEntity<?> root(@RequestBody String requestBody,
        HttpServletRequest request) {
    String result = "{\"BODY\":{},\"HEADER\":{\"RET_CODE\":0}}";
    ...
    return return new ResponseEntity<>(result, HttpStatus.OK);
}
```

### Ref
+ https://frogand.tistory.com/24
+ ...   
  

## Configuration, Properties 설정
...  
### @Configuration (예제)
- @Value, @ConfigurationProperties  


## JSON 처리
JSON/JsonNode (예제)
...  


