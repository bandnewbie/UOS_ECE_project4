# 실험 전 레포트: STM32_0_과제2 · 외부 LED로 동작시키기

작성자: 박건우 (2025440050) / 작성일: 2026-10-09 / 소스 커밋: [65c0e73](https://github.com/bandnewbie/UOS_ECE_project4/commit/65c0e732cf25f745889f9103801a15bdc25849e7) / 보드: NUCLEO-G474RE / 제공 프로젝트: ece2_474 v1.1.0

## 목적과 예상 동작

과제1 코드를 수정해 내장 LED 대신 PB0에 연결한 외부 LED로 같은 동작(1 → 2 → 4 → 8 → 1초)을 구현한다 [1].

## 소스와 연결

- 소스: [과제2_ece2_474_routine.c](../../stm32_0_tasks/과제2_ece2_474_routine.c). 실행할 때 `stm32_lab/Core/Src/ece2_474_routine.c`에 덮어쓴다.
- 과제1과 다른 곳은 LED 핀 매크로 두 줄뿐이다.

```c
#define TASK_LED_GPIO_Port GPIO_OUT1_ece2_GPIO_Port
#define TASK_LED_Pin       GPIO_OUT1_ece2_Pin
```

- 연결: PB0 → 저항(330 Ω~1 kΩ) → LED 긴 다리(+), LED 짧은 다리(−) → 보드 GND [1]
- PB0는 초기 LOW이므로 시작할 때 꺼져 있다가 1초 뒤 처음 켜진다 [1].

## 사전 확인

같은 프로젝트에 과제2 코드를 넣어 ARM GCC로 컴파일했을 때 오류와 경고가 없었다. 보드용 빌드와 다운로드는 실험 당일 수행한다.

## 보드 실험 계획

과제1을 먼저 확인한 뒤 진행한다. 외부 LED에서 간격 변경까지 확인하고 영상으로 기록한다 [1]. 영상은 `evidence/task2/board/`에 넣는다.

## 참고문헌

[1] 이해리, "STM32 실습 매뉴얼(STM32_0 · LED와 버튼, FPGA 추가 실습)" 및 "STM32 실습 안내", 서울시립대학교 전자전기컴퓨터설계실험Ⅱ, GitHub Glaysia/ece2_474 v1.1.0, 2026.

[2] D. M. Harris and S. L. Harris, *Digital Design and Computer Architecture: ARM Edition*, Morgan Kaufmann, 2015. ISBN 978-0-12-800056-4.
