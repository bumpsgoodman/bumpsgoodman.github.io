---
layout: post
title: c++ 코딩 표준 (2024-06-29 수정)
category: coding-standard
---

## UWEngine C++ 코딩 표준

게임 엔진을 만들면서 한 번쯤 정리를 해야 할 것 같아 규칙을 조금씩 추가할 예정입니다.

**언제든 수정될 문서입니다.**

## 수정 내역
- 2024-06-29: 참조 문서 및 이름 관련 표준 작성

## 참조문서
- [C++ 코딩 표준 - Pope Kim](https://docs.popekim.com/ko/coding-standards/cpp)

## 코딩 표준
1. 구조체/열거형 이름은 upper case와 snake case를 따른다.
    ```cpp
    struct SOME_STRUCTURE
    {
        // ...
    };
    ```

1. 클래스 이름은 pascal case를 따른다.
    ```cpp
    class SomeClass
    {
        // ...
    };
    ```

1. 인터페이스 선언 시 접두사 'I'를 붙인다.
    ```cpp
    class ISomeInterface
    {
        // ...
    };
    ```

1. 함수 이름은 pascal case를 따른다. 단, private 멤버 함수인 경우 camel case를 따른다.
    ```cpp
    void SomeFunction()
    {
        // ...
    }

    // private 멤버 함수
    void someFunction() 
    {
        // ...
    }
    ```

1. 지역 변수(매개 변수 포함)는 camel case를 따른다. 단, 멤버 변수인 경우 추가적으로 접두사 'm_'을 붙인다.
    ```cpp
    void SomeFunction(const int a, const int b)
    {
        const int sum = a + b;
    }

    int m_someVariable; // 멤버 변수
    ```

1. bool 변수는 접두사 'b'를 붙인다.
    ```cpp
    bool bFound;
    bool mb_found;  // private 멤버 변수
    ```

1. 포인터 변수는 접두사 'p'를 붙인다.
    ```cpp
    int num = 10;
    int* pNum = &num;
    int** ppNum = &pNum;
    ```

1. 기본적으로 모든 변수는 const를 붙인다. 변경이 필요할 때 const를 없앤다.
    ```cpp
    const int num1 = 1;
    const int num2 = 2;
    int result = 3;

    result += num1 + num2;
    ```

1. 모든 상수는 upper case와 snake case를 따른다. 단, 열거형인 경우 추가적으로 접두사로 열거형 이름을 붙인다.
    ```cpp
    #define WINDOW_WIDTH 8
    constexpr int WINDOW_HEIGHT = 8;

    enum ANIMAL_TYPE
    {
        ANIMAL_TYPE_MAMMAL,
        ANIMAL_TYPE_REPTILE
    };
    ```

1. goto 레이블명은 접두사 'lb_'와 lower case, snake case를 따른다.
    ```cpp
    lb_exit_loop:
    ```

1. 반환 값은 아래와 같은 의미를 지닌다.

    |   타입    |   의미    |
    |   :---:   |   :---:   |
    **void**    |       **절대 실패하지 않는다.**|
    **bool**    |       성공 시 **true**, 실패 시 **false**를 반환한다.|
    **void\***  |     성공 시 **유효한 주소**, 실패 시 **nullptr**을 반환한다.|
    **나머지**  |     **함수에 따라 의미가 달라진다.**|