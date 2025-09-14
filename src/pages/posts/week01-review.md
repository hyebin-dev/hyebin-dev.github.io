---
layout: ../../layouts/Layout.astro
title: "Java Week01 회고 — 오목/달팽이/시뮬레이션"
tags: [Java, StudyLog]
description: "Omok 정확히 5목 판정, 달팽이 2가지 패턴, Game of Life/Matrix 복습"
---

이번 주에는 2D 배열을 활용하는 규칙 문제를 집중적으로 풀었다.  
`OmokWinChecker`로 **정확히 5목** 판정을 구현하고(양방향 합산 + 양끝 검사로 과목 배제),  
`SnailArray`/`SnailArray2`로 달팽이 채우기를 **방문배열/경계수축** 두 방식으로 비교했다.  
`GameOfLife`는 **동시에 갱신** 원칙을 지켜 `arr → next`로 분리했고,  
`MatrixMultiplication`은 3×2·2×3 예제로 정석 삼중 루프를 점검했다.

## Omok — “정확히 5”와 과목(6+) 배제
- (x,y) 기준 4방향(→, ↓, ↘, ↗)만 검사하고, 양쪽으로 같은 색을 합산해 **정확히 5**인지 확인.  
- 이어서 **양끝 한 칸**을 확인해 같은 돌이 있으면 과목(6+)으로 무효 처리.  
- 디버깅을 위해 마지막 수를 `L`로 표시.

## Snail — 방문배열 vs 경계수축
- 방문배열: `dx/dy`와 **범위/방문 체크→회전** 한 줄 규칙으로 단순화.  
- 경계수축: `top/bottom/left/right`를 한 레이어씩 줄이며 **→ ↓ ← ↑**로 채움.  
- 둘 다 O(N²). 방문배열은 직관적, 경계수축은 메모리 추가 없음.

## Game of Life — 동시에 갱신
- 8방 이웃을 세고, **다음 세대 배열**에만 기록한 뒤 교체.  
- 규칙: (생존) 2 또는 3, (탄생) 정확히 3.

## 링크
- OmokWinChecker.java: https://github.com/hyebin-dev/java-practice/blob/main/week01/advanced/OmokWinChecker.java
- SnailArray.java: https://github.com/hyebin-dev/java-practice/blob/main/week01/advanced/SnailArray.java
- SnailArray2.java: https://github.com/hyebin-dev/java-practice/blob/main/week01/advanced/SnailArray2.java
- GameOfLife.java: https://github.com/hyebin-dev/java-practice/blob/main/week01/advanced/GameOfLife.java
- MatrixMultiplication.java: https://github.com/hyebin-dev/java-practice/blob/main/week01/advanced/MatrixMultiplication.java
