
## 7장. 객체 분해

- 탑다운 방식 (하향식 기능 분해)
  - 프로시저 추상화라고도 불림
  - 하향식 방식의 문제
    - "무엇"이 아닌 "어떻게"에 초점
    - 중앙집중 제어스타일
    - 변경이 거의 없는 설계에는 용이하나, 변경이 자주 일어나는 시스템에서는 유지보수가 어렵다.

- 정보은닉 vs 캡슐화
  - 정보은닉: 변경과 관련된 비밀을 감춘다.
  - 캡슐화: 데이터를 묶는 행위 자체, 정보은닉을 하지 않는 경우도 있다.

  - 라이브러리를 예를 들면, 퍼블릭 인터페이스(API)로 데이터를 묶어 캡슐화하여 기능을 공개하는데, 내부적으로 어떻게 구현되었는지는 프라이빗(정보은닉)하게 감출 수 있다.

- 모듈
  - 데이터를 중심으로 시스템을 분해
  - 데이터와 함수가 통합된 한 차원 높은 추상화를 제공하는 설계 단위
  - 예제) 에서는 직원로직을 모두 캡슐화

- 추상화 데이터 타입 (ADT: Abstract Data Type)
  - 데이터와 기능을 분리해서 바라본다.
  - 예제) 하나의 직원을 데이터화, 기능은 외부로 분리

- 클래스
  - 상속과 다형성 지원
  - ADT vs 클래스: ADT는 타입추상화, 클래스는 절차추상화
    - [ADT]
    - 오퍼레이션(행동 또는 기능) 기준
    - 예제) "아르바이트"와 "정규직"을 모두 "직원" 객체로 묶음

    - [클래스]
    - 타입 기준
    - 예제) 공통로직을 추상화 클래스로 공유하고, "아르바이트"와 "정규직"을 별도의 클래스로 분리
    - 공통로직: 다형성, 절차 추상화

- 개방/폐쇄 원칙
  - SOLID에서 O에 해당
  - 기존 코드에 영향을 미치지 않고, 새로운 객체 유형과 행위를 추가할 수 있는 객체지향의 특성


- 설계는 변경의 영향 정도에 따라서, "타입추가" vs "오퍼레이션 추가" 를 비교해서 진행한다.
  - 경우의 따라 장단점이 있다.
  - 일반적으로 ADT는 "데이터 중심" 설계에, 클래스는 "서비스 중심" 설계에 사용한다.




## 8장. 의존성 관리하기

- 객체지향 설계
  - 의존성 관리
  - 객체가 변화를 받아들일 수 있게 의존성을 정리하는 기술

- 의존성
  - 변경에 의한 영향의 전파 가능성을 암시

- 의존성 전이
  - A가 B에 의존하면, B가 의존하는 대상에 대해서도 의존한다는 의미
  - [PeriodCondition] ---> [Screening] ---> [Movie]

- 컴파일 의존성 vs 런타임 의존성
  - 유연하고 확장 가능한 설계를 위해 컴파일 타임 의존성과 런타임 의존성이 달라야 한다.

- 컨텍스트 독립성
  - 구체적인 문맥은 '컴파일타임 의존성'을 어떤 '런타임 의존성'으로 대체

- 의존성 해결
  - 컴파일 타임 의존성 -> 런타임 의존성으로 대체하는 방법
  
  - 1. 객체를 생성하는 시점
  - 2. 객체 생성 후, Setter 메서드를 이용
  - 3. 메서드 실행 시, 인자를 이용해서

  - * 팩토리패턴과 빌더패턴도 참고

- 유연한 설계
  - 의존성과 결합도를 고려하기
  - 바람직하지 못한 의존성: "특정한 컨텍스트"에 강하게 결합된 의존성
  - 바람직한 의존성: "재사용성" 용이, "컨텍스트"에 독립적인 의존인

- 결합도
  - 느슨한 결합도 / 약한 결합도 (지향할 것 O)
  - 단단한 결합도 / 강한 결합도 (지양할 것 X)

- 의존성 vs 결합도
  - 의존성: 두 요소 사이의 관계 유무 (O 또는 X)
  - 결합도: 의존성이 존재(O) + 의존성의 정도

- 유연한 설계를 위한 방법
  - 1. 추상화에 의존하라.
    - 인터페이스 < 추상클래스 < 구체 클래스 (결합도 정도)

  - 2. 명시적인 의존성
    - 퍼블릭 인터페이스에 노출시키기
    - 의존성을 구현 내부에 두지 말기

  - 3. new는 해롭다
    - 어떤 인자가 필요한지
    - 인자의 순서는 어떤지
    - 인자로 사용하는 구체 클래스에 대한 의존도는 어떤지
    - 고려할 점이 많다.




## 번외(기타)
  - 프론트 개발을 진행할 때, 어떻게 설계를 시작하는 가?
  - hooks는 순수 비즈니스 로직만 관심사로 두어야 하는 가? 관련 UI를 반환하면 안되는 가?
  - ADT와 클래스 기반 설계를 프론트에 어떻게 적용해볼 수 있을까?
    - 프론트에서 어떻게 컴포넌트를 상속할 수 있는가? (HOC, 컴포넌트 합성)
  - UML 다이어그램을 프론트 설계에 어떻게 적용해볼 수 있을까?
    - 개발 방법론적인 이야기도 나옴 (폭포수, 애자일, FD: Function Design, 고객요구사항 정리)
  - MVC? MVVM?
  - 리액트가 추구하는 철학은?
    - 컴포넌트 합성
    - 함수형 프로그래밍 (FP)
  - 팩토리패턴과 빌더패턴을 프론트에서 어떻게 적용해볼 수 있을까?

  