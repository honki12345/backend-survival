# DTO

### 1. DTO

**DTO (Data Transfer Object) 란**

* 원격 파사드와 같은 원격 인터페이스는 호출 비용이 상당히 부담스럽다 따라서 호출 횟수를 줄여야한다 -> 각 호출에서 더 많은 데이터를 전송해야한다 -> 다수의 매개변수 사용하기
* 호출에 필요한 모든 데이터를 저장하는 데이터전송객체를 만들어 사용
* 데이터 전송 객체는 직렬화가 가능해야 전송할 수 있다

**프로세스 간 통신(IPC, Inter-Process Communication)**

* IPC란 프로세스들 사이에 서로 데이터를 주고 받는 행위 또는 방법

**"무기력한 도메인 모델"이란 그리고 안티패턴인 이유**

* anemic 객체는 어떠한 동작(behavior)이 없고 단순한 getter setter에 불과하다
* anemic 객체는 데이터와 프로세스를 결합하는 객체지향설계의 개념에 상반된다

**자바빈즈(JavaBeans)**

**EJB(Enterprise JavaBeans)**

**Java의 record**

* 자바 14 이전에는 객체 간에 불변데이터를 주고 받는 일에 클래스를 만들어 사용해왔다
  * 쿼리결과 같은 데이터(전송을 위한 (불변)) 클래스를 작성해왔다
  * (불변) 데이터 클래스를 위해서는 다음의 규칙을 따라야한다
    1. 각 필드마다 final, private 지정
    2. 각 필드마다 getter 생성
    3. 필드와 매칭되는 적절한 생성자
    4. 필드를 사용하여 hashCode, equals, toString
* record는 필드의 유형과 이름만 쓰면되는 불변 데이터 클래스이다
  * 컴파일러에 의해 equals, hashCode, toString 메소드와 private, final 필드와 생성자가 만들어진다
  *   생성자 `public record Person (String name, String address) {}`

      ```java
      public Person(String name, String address) {
          this.name = name;
          this.address = address;
      }
      ```
  *   getter 필드 이름과 일치하는 getter 메서드 생성

      ```java
      @Test
      void givenValidNameAndAddress_whenGetNameAndAddress_thenExpectedValuesReturned() {
          String name = "John Doe";
          String address = "100 Linda Ln.";
          
          Person person = new Person(name, address);
          
          assertEquals(name, person.name());
          assertEquals(address, person.address());
      }
      ```
  *   equals, hashCode 모든 필드의 값이 일치하는 경우 true를 반환

      ```java
      @Test
      void givenSameNameAndAddress_whenEquals_thenPersonsEqual() {
          String name = "John Doe";
          String address = "100 Linda Ln.";
          
          Person person1 = new Person(name, address);
          Person person2 = new Person(name, address);
          
          assertTrue(person1.equals(person2));
      }
      ```
  * toString `Person[name=John Doe, address=100 Linda Ln.]`
  * static 변수와 메서드 추가가능

**DAO**

**ORM**
