---
layout: post
title: 소프트웨어 테스팅 용어 정리
category: software-testing
---

__*경고! 이 글은 정확한 정의를 하고 있지 않습니다. 믿지 마세요.*__

## 수정 내역
**2024-07-04 22:52:10**: 최초 작성

**2024-07-17 21:57:16**: 예제 추가

## 용어 정리

- **Driver**: 테스트할 함수를 실행하기 위해 만들어진 함수

    ```cpp
    void SomeFunc(int param)
    {
        // Some logic
    }

    // Driver 함수
    void SomeFunc_Driver(void)
    {
        int someFuncParam = 5;
        SomeFunc(someFuncParam);
    }

    ```

- **Stub**: 외부에 있는 함수는 내부를 알 수 없기 때문에 정해진 결과를 반환하는 가짜 함수
    ```cpp
    extern int ExternFunc(int param);   // 내부를 알 수 없음

    // Stub 함수
    int ExternFunc_Stub(int param)
    {
        return 0;
    }
    ```

- **Symbolic 변수**: SPF 논리식에서의 변수, Symbolic 변수로 설정되지 않은 다른 변수들은 값이 바뀌지 않음

- **Unreachable 코드**: 도달할 수 없는 코드
    ```cpp
    void SomeFunc(void)
    {
        int a = 1;
        if (a == 1)
        {
            if (a != 1)
            {
                // 절대 해당 if문을 수행할 수 없음
            }
        }
    }
    ```