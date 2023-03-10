# Chapter 01. 단위 테스트의 목표
- - -

## 단위 테스트의 목표
* 코드베이스에 대해 단위 테스트 작성이 필요하면 일반적으로 더 나은 설계로 이어진다.
  * 하지만 단위 테스트의 주목표는 아니다.
  * 더 나은 설계는 단지 좋은 부수 효과일 뿐이다.
* 단위 테스트의 목표는 소프트웨어 프로젝트의 지속 가능한 성장을 가능하게 하는 것이다.
* 개발 속도가 빠르게 감소하는 현상을 소프트웨어 엔트로피라고도 하는데, 코드베이스에서 무언가를 변경할 때마다 엔트로피는 증가한다.
  * 지속적인 정리와 리팩터링 등과 같은 적절한 관리가 필요하다.
* 테스트는 새로운 기능을 도입하거나 새로운 요구 사항에 더 잘 맞게 리팩터링한 후에도 기존 기능이 잘 동작하는지 확인하는 데 도움이 된다.

### 좋은 테스트와 좋지 않은 테스트를 가르는 요인
* 단위 테스트가 프로젝트 성장에 도움이 되는 것은 맞지만, 테스트를 작성하는 것만으로는 충분하지 않다. (잘못 작성한 테스트는 여전히 같은 결과를 낳는다.)
* 테스트의 가치와 유지 비용을 모두 고려해야 한다. 비용 요소는 다음과 같은 다양한 활동에 필요한 시간에 따라 결정된다.
  * 기반 코드를 리팩터링할 대 테스트도 리팩토링하라.
  * 각 코드 변경 시 테스트를 실행하라.
  * 테스트가 잘못된 경고를 발생시킬 경우 처리하라.
  * 기반 코드가 어떻게 동작하는지 이해하려고 할 때는 테스트를 읽는 데 시간을 투자하라.

## 테스트 스위트 품질 측정을 위한 커버리지 지표
* 커버리지 지표는 테스트 스위트가 소스 코드를 얼마나 실행하는지를 백분율로 나타낸다.
* 커퍼리지 지표는 각기 다른 유형이 있으며, 테스트 스위트의 품질을 평가하는 데 자주 사용된다.
  * 일반적으로 커버리지 숫자가 높을수록 좋지만, 테스트 스위트 품질을 효과적으로 측정하는 데 사용될 수 없다.

### 코드 커버리지 지표에 대한 이해
* 가장 많이 사용되는 커버리지 지표로 코드 커버리지가 있다. (테스트 커버리지로도 알려져 있다.)
  * 코드 커버리지(테스트 커버리지) = 실행 코드 라인 수 / 전체 라인 수
* 코드가 작을수록 테스트 커버리지 지표는 더 좋아지는데, 이는 원래 라인 수만 처리하기 때문이다. 코드를 더 작게 해도 테스트 스위트의 가치나 기반 코드베이스의 유지 보수성이 변경되지 않는다.
* 즉, 코드 커버리지 지표는 테스트 스위트 품질을 효과적으로 처리하기 어렵다.

### 분기 커버리지 지표에 대한 이해
* 분기 커버리지는 코드 커버리지의 단점을 극복하는 데 도움이 되므로 코드 커버리지보다 더 정확한 결과를 제공한다.
* 분기 커버리지 지표는 원시 코드 라인 수를 사용하는 대신 if 문과 switch 문과 같은 제어 구조에 중점을 둔다.
  * 분기 커버리지 = 통과 분기 / 전체 분기 수

### 커버리지 지표에 관한 문제점
* 분기 커버리지로 코드 커버리지보다 더 나은 결과를 얻을 수 있겠지만, 테스트 스위트의 품질을 결정하는 데 어떤 커버리지 지표도 의존할 수 없는 이유는 다음과 같다.
  * 테스트 대상 시스템의 모든 가능한 결과를 검증한다고 보장할 수 없다.
  * 외부 라이브러리의 코드 경로를 고려할 수 있는 커버리지 지표는 없다.
  * 커버리지 지표가 의미가 있으려면, 모든 측정 지표를 검증해야 한다.
* 모든 커버리지 지표가 테스트 대상 시스템이 메서드를 호출할 때 외부 라이브러리가 통과하는 코드 경로를 고려하지 않는다.
* 커버리지 지표가 외부 라이브러리의 코드 경로를 고려해야 한다는 것이 아니라(고려하면 안 된다), 해당 지표로는 단위 테스트가 얼마나 좋은지 나쁜지를 판단할 수 없다.

### 특정 커버리지 숫자를 목표로 하기
* 100%, 90% 등 특정 커버리지 숫자를 목표로 삼기 시작하면 위험 영역으로 이어질 수 있다.
* 커버리지 지표를 보는 가장 좋은 방법은 지표 그 자체로 보는 것이며, 목표로 여겨서는 안 된다.
* 커버리지 지표는 좋은 부정 지표이지만 나쁜 긍정 지표다.
  * 커버리지 숫자가 낮으면 코드베이스에 테스트되지 않은 코드가 많다는 뜻이지만, 그렇다고 높은 숫자도 별 의미는 없다.

## 무엇이 성공적인 테스트 스위트를 만드는가?
* 테스트 스위트가 얼마나 좋은지는 자동으로 확인할 수 없고, 개인 판단에 맡겨야 한다.
* 성공적인 테스트 스위트는 다음과 같은 특성을 갖고 있다.
  * 개발 주기에 통합돼 있다.
  * 코드베이스에서 가장 중요한 부분만을 대상으로 한다.
  * 최소한의 유지비로 최대의 가치를 끌어낸다.

### 개발 주기에 통합돼 있음
* 자동화된 테스트를 할 수 있는 방법은 끊임없이 하는 것뿐이다.
* 모든 테스트는 개발 주기에 통합돼야 하고, 이상적으로는 코드가 변경될 때마다 아무리 작은 것이라도 실행해야 한다.

### 코드베이스에서 가장 중요한 부분만을 대상으로 함
* 테스트가 주는 가치는 테스트 구조뿐만 아니라 검증하는 코드에도 있다.
* 시스템의 가장 중요한 부분에 단위 테스트 노력을 기울이고, 다른 부분은 간략하게 또는 간접적으로 검증하는 것이 좋다.
  * 대부분의 애플리케이션에서 가장 중요한 부분은 비즈니스 로직(도메인 모델)이 있는 부분이다.
* 통합 테스트와 같이 일부 테스트는 도메인 모델을 넘어 코드베이스의 중요하지 않은 부분을 포함해 시스템이 전체적으로 어떻게 작동하는지 확인할 수 있다. (그러나 초점은 도메인 모델에 머물러 있어야 한다.)
* 이 지침을 따르려면 도메인 모델을 코드베이스 중 중요하지 않은 부분과 분리해야 한다. 도메인 모델을 다른 애플리케이션 문제과 분리해야 단위 테스트에 대한 노력을 도메인에만 집중할 수 있다.

### 최소 유지비로 최대 가지를 끌어냄
* 테스트를 빌드 시스템에 통합하는 것만으로는 충분하지 않으며, 도메인 모델에 높은 테스트 커버리지를 유지하는 것도 충분하지 않다.
* 가치가 유지비를 상회하는 테스트만 스위트에 유지하는 것이 좋다.
  * 가치 있는 테스트와 가치가 낮은 테스트 식별하기
  * 가치 있는 테스트 작성하기 (또는 리팩터링해서 더 가치 있게 만들기)
