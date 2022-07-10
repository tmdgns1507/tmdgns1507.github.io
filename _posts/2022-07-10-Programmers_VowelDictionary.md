---
layout: single
title: "Programmers#VowelDictionary"
---

## 모음사전

링크 : https://school.programmers.co.kr/learn/courses/30/lessons/84512



### **문제 설명**

사전에 알파벳 모음 'A', 'E', 'I', 'O', 'U'만을 사용하여 만들 수 있는, 길이 5 이하의 모든 단어가 수록되어 있습니다. 사전에서 첫 번째 단어는 "A"이고, 그다음은 "AA"이며, 마지막 단어는 "UUUUU"입니다.

단어 하나 word가 매개변수로 주어질 때, 이 단어가 사전에서 몇 번째 단어인지 return 하도록 solution 함수를 완성해주세요.

##### **제한사항**

- word의 길이는 1 이상 5 이하입니다.
- word는 알파벳 대문자 'A', 'E', 'I', 'O', 'U'로만 이루어져 있습니다.



##### 입출력 예

| word      | result |
| --------- | ------ |
| `"AAAAE"` | 6      |
| `"AAAE"`  | 10     |
| `"I"`     | 1563   |
| `"EIO"`   | 1189   |

##### 입출력 예 설명

입출력 예 #1

사전에서 첫 번째 단어는 "A"이고, 그다음은 "AA", "AAA", "AAAA", "AAAAA", "AAAAE", ... 와 같습니다. "AAAAE"는 사전에서 6번째 단어입니다.

입출력 예 #2

"AAAE"는 "A", "AA", "AAA", "AAAA", "AAAAA", "AAAAE", "AAAAI", "AAAAO", "AAAAU"의 다음인 10번째 단어입니다.

입출력 예 #3

"I"는 1563번째 단어입니다.

입출력 예 #4

"EIO"는 1189번째 단어입니다.







### 풀이방법


A		1	00001
AA		2	00011
AAA		3	00111
AAAA	4	01111
AAAAA	5	11111
AAAAE	6	11112
AAAAI	7	11113
AAAAO	8	11114
AAAAU	9	11115

AAAEA	10	11161
AAAEE	11	11162
AAAEI	12	11163
AAAEO	13	11164
AAAEU	14	11165

AAAOA	15	111 '11' 1
AAAOE	16	111 '11' 2

이 규칙으로 , AEIOU 다섯개의 문자만을 사용해서 각 자리의 Index값을 알아내는 규칙을 찾으면 이 문제를 풀 수 있을 것이다. 따라서,
indexPatternList[0] = 1
indexPatternList[1] = 6
indexPatternList[2] = 31
indexPatternList[i] = [i - 1] * 5 + 1

와 같은 규칙을 갖고,


string strPattern = "AEIOU";
int wordIndex = strPattern.IndexOf(word[i]);
wordIndex* indexPatternList[i] + 1

이 방식으로 주어진 문자열이 의미하는 정수를 구해낼 수 있다.



Code (C#)

```c#
using System;
using System.Collections.Generic;

public class Solution {
    public List<int> GetIndexPattern()
        {
            List<int> _indexPatterns = new List<int>();
            _indexPatterns.Add(1);

            for (int i =1; i<5; i++)
            {
                _indexPatterns.Add(_indexPatterns[i - 1] * 5 + 1);
            }

            return _indexPatterns;
        }

        public int solution(string word)
        {
            string strPattern = "AEIOU";            
            int answer = 0;

            List<int> indexPatternList = GetIndexPattern();
            indexPatternList.Reverse();

            for(int i =0; i<word.Length; i++ )
            {
                int wordIndex = strPattern.IndexOf(word[i]);
                answer += wordIndex * indexPatternList[i] + 1;
            }

            return answer;            
        }
}
```

