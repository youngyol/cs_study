#JDBC

> JAVA 프로그램에서SQL문을실행하여 데이터를 관리하기 위한 JAVA API입니다.
>
> JDBC의특징은 다양한 데이터 베이스에 대해서 별도의 프로그램을 만들 필요 없이, 해당데이터 베이스의 JDBC를이용하면 하나의 프로그램으로 데이터 베이스를 관리할 수 있습니다.



#### 연결과정

- DB연결을 위한 Connection을 가져온다.

- SQL을 담은 Statement(또는 PreparedStatement)를 만든다.

- 만들어진 Statement를 실행

- 조회의 경우 SQL 쿼리의 실행 결과를 ResultSet으로 받아서 정보를 저장할 오브젝트에 옮겨준다.

- 작업 중에 생성된 Connection, Statement, ResultSwet 같은 리소스는 작업을 마친 후 반드시 닫아줌

- JDBC API가 만들어내는 예외(Exception)를 잡아서 직접 처리하거나, 메소드에 throws를 선언해서 예외가 발생하면 메소드 밖으로 던지게 한다.

  ```java
  public void add(User user) throws ClassNotFoundException, SQLException{
    
    Class.forName("com.mysql.jdbc.Driver");  //메모리에 OracleDriver가 로드 됩니다.
    Connection c = DriverManager.getConnection(
      			"jdbc:mysql://localhost/springbook","spring","book");
    PreparedStatement ps = c.prepareStatement("insert into users(id,name,pw) values(?,?,?)");
    ps.setString(1,user.getId());
    ps.setString(2,user.getName());
    ps.setString(3,user.getPw());
    
    ps.executeUpdate();
    
    ps.close();
    c.close();
    
  }
  ```

  ​







#### DAO , DTO 

- DAO  : DB를 사용해 데이터를 조화하거나 조작하는 기능을 전담하도록 만든 오브젝트
- DTO : 계층간 데이터 교환을 위한 자바빈즈를 말한다. 여기서 말하는 계층간의 컨트롤러, 뷰, 비즈니스 계층, 퍼시스턴스 계층을 말하며 각 계층간 데이터 교환을 위한 객체를 DTO 또는 VO라고 부른다.



[참고](http://blessldk.blogspot.kr/2015/01/spring-framework-dao.html)



### 커넥션 풀(DBCP)

클라이언트에서 다수의 요청이 발생한 경우, 데이터베이스에 부하가 발생

이러한 문제를 해결하기 위해서 커넥션 풀을 이용 (서버안에 존재 )

- 미리 커넥션을 만들어 풀에 넣어둠 

