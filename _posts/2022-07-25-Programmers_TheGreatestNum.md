---
layout: single
title: "Programmers#TheGreatestNum"
---

## 가장 큰 수

링크 : https://school.programmers.co.kr/learn/courses/30/lessons/42746



### **문제 설명**

0 또는 양의 정수가 주어졌을 때, 정수를 이어 붙여 만들 수 있는 가장 큰 수를 알아내 주세요.

예를 들어, 주어진 정수가 [6, 10, 2]라면 [6102, 6210, 1062, 1026, 2610, 2106]를 만들 수 있고, 이중 가장 큰 수는 6210입니다.

0 또는 양의 정수가 담긴 배열 numbers가 매개변수로 주어질 때, 순서를 재배치하여 만들 수 있는 가장 큰 수를 문자열로 바꾸어 return 하도록 solution 함수를 작성해주세요.

##### **제한사항**

- numbers의 길이는 1 이상 100,000 이하입니다.
- numbers의 원소는 0 이상 1,000 이하입니다.
- 정답이 너무 클 수 있으니 문자열로 바꾸어 return 합니다.


##### 입출력 예

| numbers           | return    |
| ----------------- | --------- |
| [6, 10, 2]        | "6210"    |
| [3, 30, 34, 5, 9] | "9534330" |





### 풀이방법

10이 붙어서 문자열이 되어야하는데 문제를 잘못이해해서  1, 0 떨어뜨려서 넣어줬다.

그 결과,  테스트케이스중 일부 오류가 발생했다.



Error Code (C#)

```c#
using System;
using System.Collections.Generic;

public class Solution {
   public List<string> GetNumberList(int[] numbers)
        {
            List<string> ret = new List<string>();
            foreach (int num in numbers)
            {
                int _num = num;
                while(true)
                {
                    if(_num / 10 ==0 && _num%10 > 0)
                    {
                        ret.Add((_num % 10).ToString());
                        break;
                    }
                    else if (_num /10 == 1 && _num%10 == 0)
                    {
                        ret.Add("1");
                        ret.Add("0");
                        break;
                    }

                    ret.Add((_num % 10).ToString());
                    _num /= 10;
                }
            }
            ret.Sort();
            ret.Reverse();
            return ret;
        }


        public string solution(int[] numbers)
        {
            List<string> numList = new List<string>();
            string answer = string.Empty;

            numList = GetNumberList(numbers);

            foreach (string num in numList)
            {
                answer += num;
            }
            return answer;
        }
}
```





10을 같이 넣어줘서 풀려면 10으로 반복적으로 나눠서 10보다 작은수일때의 나머지값하고 비교해야된다고 생각했다. 그러나 여기서 그 나머지 값이 여러 개가 나온다면 거기서 또 비교해야된다. (복잡성 증가)
따라서 풀이방법은 0이 아닌 숫자들을 List에 넣어주면서 넣어주는 값마다 람다함수로 Sort를 시켜주었다.  정렬시켜준 값을 String으로 더해주지 않고 StringBuilder를 사용해서 지속적으로 String변수의 메모리값을 생성시키지 않은 선에서 문자열을 이어붙였다.

아래는 정답 코드이다.



Code (C#)

```c#
using System;
using System.Collections.Generic;

public class Solution {
    class TheGreatestNumber
    {        
        public string solution(int[] numbers)
        {            
            int numLength = numbers.Length;
            List<string> strList = new List<string>();
            bool isAllZero = true;
            StringBuilder sb = new StringBuilder();
            foreach(int num in numbers)
            {
                // 0 Check
                if (num != 0)
                    isAllZero = false;

                strList.Add(num.ToString());
            }
            if (isAllZero == true) return "0";

            strList.Sort((element1, element2) => (element2 + element1).CompareTo(element1 + element2));

            foreach (string str in strList)
                sb.Append(str);

            return sb.ToString();
        }
    }
}
```

