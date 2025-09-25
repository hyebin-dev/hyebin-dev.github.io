---
title: "Tap Run — 콘솔 탭 러닝 게임 (Java)"
pubDate: 2025-09-25
description: "콘솔에서 즐기는 러닝 미니게임 3종 + 랭킹(치트 방지/정확 타이머)"
---

> 레포: [github.com/hyebin-dev/taprun](https://github.com/hyebin-dev/taprun)

![Demo](https://github.com/hyebin-dev/taprun/raw/main/assets/demo.gif)

## 개요
`Tap Run`은 콘솔에서 즐기는 **탭(Enter) 기반 런 게임** 묶음입니다.  
세 가지 모드가 있고, 기록은 파일로 저장하는 **랭킹 시스템**을 제공합니다.

- **Race Mode**: 두 플레이어가 20번의 ‘빈 Enter’ 입력 시간을 겨룹니다. (주사위로 선/후공 결정, 시작 키로 자동 시작 방지)
- **Monster Mode**: 제한 시간 안에 엔터 연타로 몬스터 HP를 0으로 만드는 라운드전(3라운드).
- **Vs AI Mode**: 난이도(EASY/NORMAL/HARD)에 따라 AI가 일정 속도로 전진. 플레이어가 이기면 랭킹 등록.

## 기술 포인트
- **치트 방지(Quiet Gap)**: 연속 입력 최소 간격으로 홀드/오토 입력 무효화.
- **정확한 타이밍**: `System.nanoTime()` 기반 측정으로 ms 단위 흔들림 최소화.
- **랭킹 설계**:  
  - 동일 이름은 **더 좋은 기록만 갱신**  
  - VsAI는 **난이도별 그룹** 정렬(EASY → NORMAL → HARD) + 시간 오름차순  
  - 화면은 Top 20만 노출, 파일에는 **전체 이력 저장**
- **UX 디테일**: 선/후공 주사위, 시작 키(1/2)로 자동 시작 방지, 진행바·HP바 출력, 잘못된 입력 방어.

## 폴더 구조
taprun/
├─ core/
│ ├─ Game.java
│ ├─ Player.java
│ ├─ Settings.java
│ ├─ RankingManager.java
│ └─ Utils.java
├─ modes/
│ ├─ RaceMode.java
│ ├─ MonsterMode.java
│ └─ VsAiMode.java
└─ Main.java

---

## ▶ 실행 방법 (JDK 11+)

Windows(CMD/PowerShell):

```bat
javac -encoding UTF-8 -d . taprun/core/*.java taprun/modes/*.java taprun/Main.java
java taprun.Main

## 🧩 내 역할 (팀 기여 요약)

- **VsAiMode 설계·구현**: 난이도별 AI TPS(EASY/NORMAL/HARD), 오른쪽→왼쪽 트랙 렌더링, 동시 골인 시 플레이어 우선 로직.
- **치트 방지(Quiet Gap)**: `System.nanoTime()` 기반 최소 입력 간격 검증으로 홀드/오토 입력 무효화.
- **정확한 타이밍**: `System.nanoTime()`로 측정(밀리초 대비 정밀), 입력 간격·완주 시점 판정.
- **랭킹 시스템 개선**  
  - 동일 이름은 **더 좋은 기록만 갱신(upsert)**.  
  - VsAI는 **난이도 고정 정렬(EASY → NORMAL → HARD)** 후 시간 오름차순.  
  - 파일에는 전체 저장, 화면에는 **Top 20만 노출**(가독성).
- **UX 안정성**: 선/후공 차례 **시작 키(‘1’, ‘2’)** 요구로 자동 시작 방지, 잘못된 입력 루프 안내.
- **예외/경계 케이스**: `Scanner` 개행 처리, 숫자 입력 `InputMismatchException` 방어, 파일 I/O 예외 메시지 분리.

---

## 📚 배운 점

- 콘솔 입력을 이벤트처럼 다루는 **상태 전환**(대기 → 진행 → 종료) 구조화.
- **파일 I/O + 정렬(Comparator)** 로 영속 데이터 정리/표시 파이프라인 구성.
- 실수 시간 비교, 경계값(동시 골인, 0/음수, 오버플로) 처리의 중요성.
- `Scanner` 공유/개행 처리 같은 **입출력 함정** 대응.

---

## 🚀 개선 계획 (우선순위)

**단기(주말)**  
1) **3-2-1 카운트다운** 후 시작(UX)  
2) **데모 GIF** 촬영 후 포스트/README 상단 배치  
3) **실행 스크립트(run.bat)** 제공(Windows 한 줄 실행)  
4) **리팩터링**: 난이도/정렬 상수 맵 정리, 공통 출력 헬퍼 추출  

---

## 🏷️ 태그
`Java`, `Console`, `OOP`, `File I/O`, `Algorithms`, `Portfolio`

