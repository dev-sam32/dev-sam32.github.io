---
title:  "[23/04/06] Inflearn_SpringCoreBasic 싱글톤 컨테이너"
excerpt: ""

categories:
  - TIL
tags:
  - [TIL, Spring]

toc: true
toc_sticky: true
 
date: 2023-04-06
last_modified_at: 2023-04-06
---
# 섹션 5. 싱글톤 컨테이너

## 싱글톤 패턴(Singleton Pattern)

- Class의 인스턴스가 단 하나만 생성되는 것을 보장하는 디자인 패턴
  - 객체 인스턴스가 2개 이상 생성되지 못하도록 설정
    - ```private``` 생성자를 사용해서 외부에서 new 키워드 사용을 막음
- 싱글톤 패턴의 문제점 ⚠️
  - 싱글톤 패턴을 위한 코드 필요
  - 의존관계상 클라이언트가 구체 클래스에 의존 -> DIP 위반, OCP원칙 위반 가능성
  - Test 어려움, private 생성자 제약
    - 유연성이 떨어짐
  - 안티패턴으로 불리기도 함

## 싱글톤 컨테이너(SIngletone Container)

- 싱글톤의 문제점을 해결하고, 객체 인스턴스를 싱글톤으로 관리해줌
- 싱글톤 패턴 주의점⚠️
  - 여러 클라이언트가 하나의 같은 객체를 공유하기 때문에 무상태(Stateless)로 설계해야함
    - 특정 클라리언트에 의존적 필드 ❌
    - 특정 클라이언트가 값을 변경할 수 있는 필드 ❌
    - 가급적 읽기만 가능해야함(Read Only)
  - 필드 대신 공유되지 않는 지역변수, 파라미터 등을 사용해야함

## @Configuration

- CGLIB 라이브러리를 통해 싱글톤을 보장 할 수 있도록 해줌