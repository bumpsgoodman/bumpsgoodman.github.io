---
layout: post
title: cpp 코딩 표준
category: coding-standard
---

최종 수정: 2024-06-29

1. 구조체/열거형 이름은 upper case와 snake case를 따른다.
    ```
    struct SOME_STRUCTURE
    {
        // ...
    };
    ```

1. 클래스 이름은 pascal case를 따른다.
    ```
    class SomeClass
    {
        // ...
    };
    ```

1. 인터페이스 선언 시 접두사 'I'를 붙인다.
    ```
    class ISomeInterface
    {
        // ...
    };
    ```

1. 함수 이름은 pascal case를 따른다. 단, private 멤버 함수인 경우 camel case를 따른다.
    ```
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
    ```
    void SomeFunction(const int a, const int b)
    {
        const int sum = a + b;
    }

    int m_someVariable; // 멤버 변수
    ```

1. bool 변수는 접두사 'b'를 붙인다.
    ```
    bool bFound;
    bool mb_found;  // private 멤버 변수
    ```

1. 포인터 변수는 접두사 'p'를 붙인다.
    ```
    int num = 10;
    int* pNum = &num;
    int** ppNum = &pNum;
    ```

1. 기본적으로 모든 변수는 const를 붙인다. 변경이 필요할 때 const를 없앤다.
    ```
    const int num1 = 1;
    const int num2 = 2;
    int result = 3;

    result += num1 + num2;
    ```

1. 모든 상수는 upper case와 snake case를 따른다. 단, 열거형인 경우 추가적으로 접두사로 열거형 이름을 붙인다.
    ```
    #define WINDOW_WIDTH 8
    constexpr int WINDOW_HEIGHT = 8;

    enum ANIMAL_TYPE
    {
        ANIMAL_TYPE_MAMMAL,
        ANIMAL_TYPE_REPTILE
    };
    ```

1. goto 레이블명은 접두사 'lb_'와 lower case, snake case를 따른다.
    ```
    lb_exit_loop:
    ```

1. 반환 값은 아래와 같은 의미를 지닌다.

    |   타입    |   의미    |
    |   :---:   |   :---:   |
    **void**    |       **절대 실패하지 않는다.**|
    **bool**    |       성공 시 **true**, 실패 시 **false**를 반환한다.|
    **void\***  |     성공 시 **유효한 주소**, 실패 시 **nullptr**을 반환한다.|
    **나머지**  |     **함수에 따라 의미가 달라진다.**|