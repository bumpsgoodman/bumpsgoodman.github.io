---
layout: post
title: 동적 심볼릭 테스팅(Concolic 테스팅)
category: software-testing
---

## Concolic 테스팅
Concolic은 **CONC**rete + symb**OLIC**의 합성어다.

입력으로 프로그램 소스를 받아 프로그램의 구조와 의미를 분석 후, 프로그램의 모든 실행 경로를 도달하도록 테스트 입력 값을 생성해내는 Whitebox 테스팅 기법이다.

SMT 해법기(Satisfiability Module Theory Solver)로 테스트 입력 값의 해를 구하여 새로운 입력 값을 생성해낸다.

## 심볼릭 환경 모델링(Symbolic Environment Modeling)
어떤 변수를 심볼릭 변수로 사용할지 결정하는 방법이다. 일반적으로 심볼릭 모델 환경은 수작업을 통해 이루어지는데, 다시 말하면 테스트 대상 소프트웨어의 도메인 지식과 동적 테스팅 기술 모두 잘 알아야 한다는 것이다.

심볼릭 경로 논리식(SPF)를 추출하는 방식은 크게 두 가지가 있다.

1. 가상 머신 기반(예: [KLEE](https://klee-se.org/))
1. 테스팅 대상 프로그램 코드에 probe를 삽입하는 방식 (예: [CROWN](https://www.vpluslab.kr/solution))

(이 둘에 대해선 나중에 정리해보자)

## SPF 조건 구문 선택(Symbolic Search Stratege)
Concolic 테스팅은 현재 추출한 SPF 안의 어떤 조건 구문을 부정하느냐에 따라 생성되는 테스트 입력 값 순서가 달라진다.
예를 들어, DFS를 사용할 수도 있고, 랜덤으로 선정할 수도 있다.

(이 외에도 다양하게 있는데 나중에 좀 더 정리하자)

## 정리
정리하자면 Concolic 테스팅이란 자동으로 모든 테스트 입력 값을 생성하고, 검증하는 것이다. (그냥 내 생각을 말한거니 틀릴 수도 있다.)

그리고 Concolic 테스팅을 하기 위해선 테스트 하고자 하는 프로그램의 소스 코드가 필요하다.

---

자동으로 모든 테스트를 한다는게 대단하지만 엄청나게 느릴 것이다. 이 분야에서 필요한 것은 엄청난 최적화인데 내가 할 수 있을까?