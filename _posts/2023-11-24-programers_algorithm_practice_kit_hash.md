---
title: (프로그래머스) 코딩테스트 고득점 Kit - 해시
date: 2023-11-24 19:40:00 +0900
categories: [coding_test, Programers, 코딩테스트_고득점_Kit, 해시, 개념]
tags: [coding_test, java, programers]     # TAG names should always be lowercase
author: hoos007
---

프로그래머스의 코딩테스트 고득점 Kit으로 공부하며 작성한 내용 입니다.


"임의의 길이의 데이터를 고정된 길이의 데이터로 매핑하는 것이다."
자료구조의 해시맵에서 인덱스값으로 사용된다.

HashMap, HashTable, HashSet, LinkedHashMap, TreeMap - 추가

대충 보니까 HashMap이 메인이고 다른것들은 특징적으로 필요할때만 사용하는듯.

## 사용하는 이유는
1. ArrayList에서 데이터를 추가하거나 삭제할때 다른 값들의 인덱스가 수정되어야 하는 경우가 있어 속도저하가 생김
2. LinkedList는 값을 검색하기 위해 처음부터 하나씩 다 확인해야 하기때문에 비효율적임

결국 효과적으로 빠르게 값을 탐색하기 위해 고안된 방법이다.

+이미 정렬 되어있는 값을 순차적으로 값을 탐색할때는 배열 구조가 더 빠르다.

## 해시맵이 자료를 저장하기 위한 방법은 두 가지가 있는데
1. Separate Chaining
2. Open Addressing
이다.

방법이 여러가지인 배경은 해시값이 충돌하는 경우가 발생하기 때문이다. 다른 데이터가 같은 해시값을 가지게 되는 경우 같은 인덱스 값에 저장할 수 없기 때문인데, 이를 해결하기 위해 두가지 방법이 존재한다.
Sparate Chaining은 서로 다른 두 데이터가 같은 인덱스를 갖게 되는경우 같은 인덱스를 사용하면서 데이터를 LinkedList로 이어서 저장하는 것이다. 이를 통해 같은 인덱스를 사용할 수 있고 HashMap의 장점도 살릴 수 있다.
Open Addressing은 같은 인덱스를 사용하게 되는경우 다른 빈자리를 찾는것이다. 이미 인덱스에 값이 존재하는경우에 하나씩 넘어가면서 빈곳을 탐색하고 발견하면 저장한다.
데이터를 무한으로 저장할 수 있는 Sparate Chaining과 다르게 이 방법은 슬롯 개수 이상으로는 저장할 수 없다.

## 자바에서는 HashMap타입을 통해 해시맵을 사용할 수 있다.

HashMap을 알기 위해서 우선 Map에 대해 정리해보자.
1. Key-Value
2. Key는 고유한 값
이것이다.

HashMap객체를 생성하는 방법
```java
HashMap<String,String> map1 = new HashMap<String,String>();//HashMap생성
HashMap<String,String> map2 = new HashMap<>();//new에서 타입 파라미터 생략가능
HashMap<String,String> map3 = new HashMap<>(map1);//map1의 모든 값을 가진 HashMap생성
HashMap<String,String> map4 = new HashMap<>(10);//초기 용량(capacity)지정
HashMap<String,String> map5 = new HashMap<>(10, 0.7f);//초기 capacity,load factor지정
HashMap<String,String> map6 = new HashMap<String,String>(){{//초기값 지정
    put("a","b");
}};
```
load factor는 HashMap이 데이터가 너무 많아지면 모든 인덱스의 값이 LinkedList처럼 될텐데 그걸 방지하기 위해 어느정도가 차면 용량을 늘릴지에 대한 값이다. 기본은 0.75이다.

값 추가
```java
HashMap.put("Key","Value");
```

값 제거
```java
HashMap.remove("Key"); //key값 제거
HashMap.clear(); //모든 값 제거
```

값 접근
```java
HashMap<Integer,String> map = new HashMap<Integer,String>(){{//초기값 지정
    put(1,"사과");
    put(2,"바나나");
    put(3,"포도");
}};
		
System.out.println(map); //전체 출력 : {1=사과, 2=바나나, 3=포도}
System.out.println(map.get(1));//key값 1의 value얻기 : 사과
		
//entrySet() 활용
for (Entry<Integer, String> entry : map.entrySet()) {
    System.out.println("[Key]:" + entry.getKey() + " [Value]:" + entry.getValue());
}
//[Key]:1 [Value]:사과
//[Key]:2 [Value]:바나나
//[Key]:3 [Value]:포도

//KeySet() 활용
for(Integer i : map.keySet()){ //저장된 key값 확인
    System.out.println("[Key]:" + i + " [Value]:" + map.get(i));
}
//[Key]:1 [Value]:사과
//[Key]:2 [Value]:바나나
//[Key]:3 [Value]:포도
```

여기서 참고함.
https://coding-factory.tistory.com/556





후에 알아보니 HashSet도 있다. 이것도 정리할것.