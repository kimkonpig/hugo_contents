---
title: "Programmers 12899 | 124 나라의 숫자"
date: 2020-07-22
tags: ["programmers", "coding", "practice", "quiz"]
draft: true
---

# <!-- Programmers 12899 | 124 나라의 숫자 -->

### 문제 설명

124 나라가 있습니다. 124 나라에서는 10진법이 아닌 다음과 같은 자신들만의 규칙으로 수를 표현합니다.

- 124 나라에는 자연수만 존재합니다. 

- 124 나라에는 모든 수를 표현할 때 1, 2, 4만 사용합니다.

예를 들어서 124 나라에서 사용하는 숫자는 다음과 같이 변환됩니다.

| 10진법 | 124 나라 | 10진법 | 124 나라 |
| ------ | -------- | ------ | -------- |
| 1      | 1        | 6      | 14       |
| 2      | 2        | 7      | 21       |
| 3      | 4        | 8      | 22       |
| 4      | 11       | 9      | 24       |
| 5      | 12       | 10     | 41       |

자연수 n이 매개변수로 주어질 때, n을 124 나라에서 사용하는 숫자로 바꾼 값을 return 하도록 solution 함수를 완성해 주세요.



### 제한사항

- n은 500,000,000이하의 자연수 입니다.



### 입출력 예

| n    | result |
| ---- | ------ |
| 1    | 1      |
| 2    | 2      |
| 3    | 4      |
| 4    | 11     |



### 풀이

1. 10진법 자연수에서 124 나라 자연수 구하는 방법 도출

2. 124 나라에서는 1, 2, 4의 **세가지 숫자**만 사용하여 모든 수를 표현

3. 10진법 자연수를 3으로 나눈 나머지와 124 나라 자연수와 맵핑  

   <3 이하의 수>

   

   - 10진법 자연수 **1** -> 3으로 나눈 나머지 *1* -> 124 나라 자연수 **1**

   

   - 10진법 자연수 **2** -> 3으로 나눈 나머지 *2* -> 124 나라 자연수 **2**

   

   - 10진법 자연수 **3** -> 3으로 나눈 나머지 *0* -> 124 나라 자연수 **4**  

   

   ```  java
   /* 나머지를 인덱스로, 124 나라의 세가지 숫자를 원소로 갖는 배열 생성 */
   String[] arr = {"4", "1", "2"}
   ```

   <3 이상의 수>

   

   - 10진법 자연수 **4** -> 3으로 나눈 나머지 1 AND 4 / 3 = 1을 3으로 나눈 나머지 1 -> 124 나라 자연수 **11**

   

   - 10진법 자연수 **5** -> 3으로 나눈 나머지 2 AND 5 / 3 = 1을 3으로 나눈 나머지 1 -> 124 나라 자연수 **12**

   

   - **(주의)** 10진법 자연수 **6** -> 3으로 나눈나머지 0 AND 6 / 3 = 2를 3으로 나눈 나머지 2 -> 124 나라 자연수 *24*가 아니라 **14**가 나와야 한다.

   

   - 즉 3으로 나누어 떨어지는 매개변수(10진법 자연수)는 -1을 해줘야 원하는 값이 나온다.

   마지막으로 연산결과는 뒤에서 앞으로 붙여야 한다. (10진법 자연수 5, 6 참고)



### 코드

```java
class Solution {
    public String solution(int n) {
        String answer = "";
        String[] numbers = {"4", "1", "2"};
        
        while(n > 0){
            int rnum = n % 3; //3으로 나눈 나머지 구하기
            n = n / 3;
            if(rnum == 0) n--; //3으로 나누어 떨어지는 값은 -1 해주기
            answer = numbers[rnum] + answer; //연산결과(맵핑값)은 뒤에서 앞으로 붙여주기
        }
        return answer;
    }
}
```







