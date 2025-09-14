---
layout: ../../layouts/Layout.astro
title: "Java Week01 피드백 — 오목·달팽이·시뮬레이션"
tags: [Java, StudyLog]
description: "정확히 5목 판정, 달팽이 2가지 패턴, Game of Life/Matrix 복습"
---

이번 주는 2D 배열과 규칙 기반 문제를 중심으로 손을 풀었습니다.  
`OmokWinChecker`로 **정확히 5목**을 판정하는 흐름(양방향 합산 + 양끝 검사)을 정리했고,  
`SnailArray / SnailArray2`로 달팽이 채우기를 **방문배열/경계 수축** 두 방식으로 비교했습니다.  
`GameOfLife`는 **동시에 갱신** 원칙대로 현재/다음 세대를 분리했고,  
`MatrixMultiplication`은 3×2·2×3 예제로 삼중 루프를 점검했습니다.

## Omok — “정확히 5”와 과목(6+) 배제
- (x,y)을 기준으로 4방향(→, ↓, ↘, ↗)만 검사하고 양쪽 길이를 합산합니다.  
- 합이 5여도 **양끝 한 칸**을 확인해 같은 돌이 있으면 과목(6+)으로 무효 처리합니다.  
- 디버깅을 위해 마지막 수를 `L`로 표시했습니다.

## Snail — 방문배열 vs 경계 수축
- 방문배열: `dx/dy`와 **범위/방문 체크→회전** 규칙으로 단순화.  
- 경계 수축: `top/bottom/left/right`를 줄이며 **→ ↓ ← ↑**로 채움.  
- 두 방식 모두 O(N²). 직관성(방문배열) vs 메모리 절약(경계 수축).

## Game of Life — 동시에 갱신
- 8방 이웃을 세고, **다음 세대 배열**에 기록한 뒤 교체합니다.  
- 규칙: (생존) 2 또는 3 / (탄생) 정확히 3.

## 링크
- OmokWinChecker.java: https://github.com/hyebin-dev/java-practice/blob/main/week01/advanced/OmokWinChecker.java
- SnailArray.java: https://github.com/hyebin-dev/java-practice/blob/main/week01/advanced/SnailArray.java
- SnailArray2.java: https://github.com/hyebin-dev/java-practice/blob/main/week01/advanced/SnailArray2.java
- GameOfLife.java: https://github.com/hyebin-dev/java-practice/blob/main/week01/advanced/GameOfLife.java
- MatrixMultiplication.java: https://github.com/hyebin-dev/java-practice/blob/main/week01/advanced/MatrixMultiplication.java
