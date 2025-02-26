---
layout: post
title: 리팩터링 1장
---

1장에서는 리팩터링의 필요성과 준비해야될 장치들을 언급한다.

>'디지털 시대의 연약한 자여, 그대 이름은 소프트웨어'

잘 작동하고 나중에 변경할 일이 절대 없다면 코드를 기준 상태로 놔두어도된다.
누군가 코드를 읽지 않는 한 아무런 피해가 없다.

>'프로그램이 새로운 기능을 추가하기에 편한 구조가 아니라면, 먼저 기능을 추가하기 쉬운 형태로 리팩터링하고 나서 원하는 기능을추가한다.'

리팩터링의 첫 단계는 항상 테스트 작성해두는 것이다.
리팩터링 기법들이 버그 발생 여지를 최소화하도록 구성됐다고는 하나 실제 작업은 사람이 수행한다.

테스트는 내가 저지른 실수로부터 보호해주는 버그 검출기의 역활을 하며,
테스트 작성에 시간을 들겠지만 신경써서 만들었다면 오히려 디버깅 시간이 줄어 전체 작업 시간은 단축된다.

긴 함수를 리팩터링할 때는 전체 동작을 각각의 부분으로 나눌 수 있는 지점을 찾는다.
부분으로 나눈 스니펫 코드를 함수로 추출하고 적당한 이름을 붙인다.

이런 작은 변화라도, 항상 잘 작동하는지 테스트를 실행해본다.

>'리팩터링은 프로그램 수정을 작은 단계로 나눠 진행한다. 그래서 중간에 실수하더라도 버그를 쉽게 찾을 수 있다.'

후에, 깃으로 변경사항을 커밋하여 하나하나 작업의 완결성을 부여한다. ( 작은 단위로 작업하기 )

1장에서 이용한 4단계의 리팩토링 기법은 이렇다.

* __반복문 쪼개기__로 변수 값을 누적시키는 부분을 분리한다.
* __문장 슬라이드하기__로 변수 초기화 문장을 변수 값 누적 코드 바로 앞으로 옮긴다
* __함수 추출하기__로 계산 부분을 별도의 함수로 추출한다.
* __변수 인라인하기__로 지역변수들을 함수로 return하게하여, 인라인화 한다.

그외에도 반복문에 대한 이야기가 나오는데,
한 반복문 내에서 너무 많은 것을 수행하고 있다면 반복문을 2번써서라도
해당 로직을 분리한다. (일반적으로는 큰 성능 차이는 없으나, 특정 상황은 고려해야된다.)

함수를 어느정도 추출하였다면, __단계 쪼개기__르 한다.
실제 외부에서 실행될 함수(혹은 단계)가 너무 복잡하다면, 그 단계를 쪼갠다.
(책에서는 예로 데이터 처리부분과 HTML랜더를 같이하는 함수를 두개로 분리해낸다, 그리고
실제 데이터를 처리하는 부분은 조각난 데이터 변수들을 모아서 객체로 리턴해주는 중간 데이터 함수를
만들어 사용한다.)
