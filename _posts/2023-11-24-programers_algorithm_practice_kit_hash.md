---
title: [프로그래머스] 코딩테스트 고득점 Kit - 해시
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