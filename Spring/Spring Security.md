- 스프링 기반의 어플리케이션의 보안(인증과 권한)을 담당하는 프레임워크
	- 만약 스프링 시큐리티를 사용하지 않았다면, 자체적으로 세션을 체크하고 리다이렉트 등을 해야 함
- 필터(Filter) 기반으로 동작하기 때문에 스프링 MVC 와 분리되어 관리 및 동작
## Spring Security Architecture
### Filters
클라이언트(보통 브라우저)는 요청을 보내고 되고, 그 요청을 서블릿이나 JSP등이 처리하게 됩니다. 
스프링 MVC에서는 요청을 가장 먼저 받는 것이 DispatcherServlet이라고 했었습니다.  
이 DispatcherServlet이 요청 받기 전에 다양한 필터들이 있을 수 있습니다.  
필터가 하는 역할은 클라이언트와 자원 사이에서 요청과 응답 정보를 이용해 다양한 처리를 하는데 목적이 있습니다. 어떤 필터는 요청을 받은 후, 클라이언트가 원래 요청한 자원이 아닌 다른 자원으로 리다이렉트 시킬 수도 있습니다. 어떤 필터는 다음 필터에게 요청과 응답을 전달하지 않고, 바로 클라이언트에게 응답하고 끝낼 수도 있습니다.
`FilterChain`: 여러 개의 필터가 연결된 필터 사슬
### DelegatingFilterProxy
 서블릿 컨테이너는 `Filter`를 등록하게 해주지만, 스프링은 이를 빈으로 인식하지 않는다. 따라서 관리를 하지 못한다. 이 문제를 해결하기 위해 `DelegatingFilterProxy`를 사용한다.
 `DelegatingFilterProxy`는 `ApplicationContext`에서 `Bean Filter`를 찾아서 실행한다. 이 말인 즉슨 `DelegatingFilterProxy` 자체는 인증, 인가를 하지 않는다는 의미다. 그저 `Filter` 인터페이스를 상속받은 스프링 빈을 **Delegate**하는 중간다리 역할일 뿐이다. (Delegate = 대리자)
### FilterChainProxy
`FilterChainProxy`는 보통 스프링 빈이기 때문에 `DelegatingFilterProxy`로 감싸져 있다. 주요 역할은 요청에 따라 필요한 필터를 실행시키는 것인데, `DelegatingFilterProxy`와 마찬가지로 어떤 로직을 수행한다기보다는 위임자의 역할을 수행한다.
### SecurityFilterChain
`SecurityFilterChain`는 `FilterChainProxy`가 요청에 따라 어떤 필터 체인을 실행시켜야할지 파악하는데 쓰인다.
![[Pasted image 20240320144336.png]]

### Security Filters
![[Pasted image 20240320144900.png]]
![[Pasted image 20240320144919.png]]
* SecurityContextPersistenceFilter : SecurityContextRepository에서 SecurityContext를 가져오거나 저장하는 역할을 한다.  
  * LogoutFilter : 설정된 로그아웃 URL로 오는 요청을 감시하며, 해당 유저를 로그아웃 처리  
  * (UsernamePassword)AuthenticationFilter : (아이디와 비밀번호를 사용하는 form 기반 인증) 설정된 로그인 URL로 오는 요청을 감시하며, 유저 인증 처리  
        1. AuthenticationManager를 통한 인증 실행  
        2. 인증 성공 시, 얻은 Authentication 객체를 SecurityContext에 저장 후 AuthenticationSuccessHandler 실행  
        3. 인증 실패 시, AuthenticationFailureHandler 실행  
  * DefaultLoginPageGeneratingFilter : 인증을 위한 로그인폼 URL을 감시한다.  
  * BasicAuthenticationFilter : HTTP 기본 인증 헤더를 감시하여 처리한다.  
  * RequestCacheAwareFilter : 로그인 성공 후, 원래 요청 정보를 재구성하기 위해 사용된다.  
  * SecurityContextHolderAwareRequestFilter : HttpServletRequestWrapper를 상속한 SecurityContextHolderAwareRequestWapper 클래스로 HttpServletRequest 정보를 감싼다. Security  ContextHolderAwareRequestWrapper 클래스는 필터 체인상의 다음 필터들에게 부가정보를 제공한다.  
  * AnonymousAuthenticationFilter : 이 필터가 호출되는 시점까지 사용자 정보가 인증되지 않았다면 인증토큰에  사용자가 익명 사용자로 나타난다.  
  * SessionManagementFilter : 이 필터는 인증된 사용자와 관련된 모든 세션을 추적한다.  
  * ExceptionTranslationFilter : 이 필터는 보호된 요청을 처리하는 중에 발생할 수 있는 예외를 위임하거나 전달하는 역할을 한다.  
  * FilterSecurityInterceptor : 이 필터는 AccessDecisionManager 로 권한부여 처리를 위임함으로써 접근 제어 결정을 쉽게해준다.
### Handling Security Exceptions
`ExceptionTranslationFilter`는 _**AccessDeniedException**과 **AuthenticationException**을 HTTP 응답으로 변환해준다.
![[Pasted image 20240320144650.png]]

출처:
https://velog.io/@kai6666/Spring-%EC%8A%A4%ED%94%84%EB%A7%81-%EC%8B%9C%ED%81%90%EB%A6%AC%ED%8B%B0Spring-Security-%EA%B8%B0%EB%B3%B8-%EA%B0%9C%EB%85%90%EA%B3%BC-%EA%B5%AC%EC%A1%B0
https://m.boostcourse.org/web326/lecture/58997