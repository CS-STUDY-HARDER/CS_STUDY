# Spring MVC
---

## Spring MVC 동작 과정
- 스프링 MVC는 DispatcherServlet, View Resolver, Interceptor, Handler, View 등으로 구성
- DispatcherServlet이 Front-Controller 역할
- 동작 과정
    1) 요청(request)이 들어온다
    2) 웹 컨테이너는 DispatcherServlet 객체를 생성하고, 초기화 (첫 호출시)
    3) 웹 컨테이너가 Request, Response 객체를 생성
    4) 웹 컨테이너의 쓰레드 풀에서 쓰레드 하나를 할당하여 DispatcherServlet 실행
    5) DispatcherServlet이 모든 요청을 받는다
    6) DispatcherServlet은 요청 URL을 HandlerMapping 객체에 넘기고 호출해야할 Controller 메소드 정보를 얻는다
    7) DispatcherServlet이 HandlerAdapter 객체를 가져온다
    8) DispatcherServlet이 HandlerAdapter 객체의 메소드를 실행
    9) Controller 객체는 처리를 하고 Model에 뷰에 전달할 객체를 저장하고, DispatcherServlet에 view name을 리턴
    10) DispatcherServlet은 view name을 View Resolver에 전달하여 View 객체를 얻는다
    11) View객체는 해당하는 화면 뷰를 호출하고, Model객체에서 화면 표시에 필요한 객체를 가져와서 화면 표시를 처리한다

- 실질적으로 Controller를 실행하는것은 Handler Adapter
- DispatcherServlet도 Servlet의 라이프 사이클(init, service, destory)을 따른다

### Spring MVC의 context


---
## 출처
https://jeonyoungho.github.io/posts/Spring-MVC-%EB%8F%99%EC%9E%91-%EA%B3%BC%EC%A0%95/
https://velog.io/@hyeminn/Spring-Spring-MVC-%EB%8F%99%EC%9E%91-%EC%9B%90%EB%A6%AC
https://starkying.tistory.com/entry/Spring-MVC-%EB%8F%99%EC%9E%91%EC%9B%90%EB%A6%AC-%EA%B5%AC%EC%84%B1%EC%9A%94%EC%86%8C
https://live-everyday.tistory.com/164
https://velog.io/@seculoper235/Spring-Core-Context-1%ED%8E%B8
---