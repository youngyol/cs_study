#### JSP 태그의 개념 이해

- Servlet은JAVA언어를이용하여 문서를 작성하고, 출력객체를이용하여 HTML코드를삽입
- JSP는Servlet과반대로 HTML코드에 JAVA언어를삽입하여 동적 문서를 만들고, HTML코드안에JAVA코드를삽입하기 위해서는 태그를 이용

지시자 : <%@  %> : 페이지 속성 <br/>

주석 : <%-- --%> (소스보기해도 안보인다. HTML주석은 보임 왜? JSP는 WAS에서 처리하고 클라이언트에는 HTML파일로 가기때문) <br/>

선언 : <%! %> : 변수 메소드 선언 , 전역의미<br/> 

표현식 : <%=  %> : 결과값 출력  <br/>

스크립트릿 : <%    %> : Java코드  <br/>



#### JSP 동작원리 

- 클라이언트가 웹브라우저로 helloWorld.jsp를 요청하게 되면 JSP컨테이너가 JSP파일을 Servlet파일(.java)로 변환
- Servlet파일(.java)은컴파일 된 후 클래스 파일(.class)로변환되고, 요청한클라이언트한테 html파일형태로 응답



#### JSP 내부객체

개발자가객체를 생성하지 않고 바로 사용할 수 있는 객체가 내부객체 , JSP에서제공되는 내부객체는 JSP컨테이너에의해 Servlet으로변화될 때 자동으로 객체가 생성



- 입출력객체 : request, response, out
- 서블릿객체 : page, config
- 세션 객체: session
- 예외 객체: exception

