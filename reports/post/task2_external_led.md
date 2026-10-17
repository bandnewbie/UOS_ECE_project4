# 실험 후 레포트: STM32_0_과제2 · 외부 LED로 동작시키기

작성자: 박건우 (2025440050) / 실험일: 2026-10-12 / 제출 태그: `lab4-post` / 수행 PC: 조원 노트북(SangHyeok) / 보드: NUCLEO-G474RE

## 설계

과제1 코드에서 LED 매크로 두 줄만 PB0(`GPIO_OUT1_ece2_GPIO_Port`, `GPIO_OUT1_ece2_Pin`)으로 바꿨다 [1]. 배선: PB0 → 저항 → LED(+), LED(−) → GND.

- 코드: [과제2_ece2_474_routine.c](../../stm32_0_tasks/과제2_ece2_474_routine.c)
- 보드 실행본: [조원노트북_실행본_ece2_474_routine.c](../../stm32_0_tasks/조원노트북_실행본_ece2_474_routine.c) (PB0 설정)

## 보드 확인

| 확인 항목 | 예상 | 실측 |
|---|---|---|
| 시작 직후 | 꺼짐 → 1초 뒤 켜짐 (PB0 초기 LOW) | 일치 (영상) |
| 버튼 누름 | 1 → 2 → 4 → 8 → 1초 | 일치 (영상) |
| 내장 LED(PA5) | 변화 없음 | 일치 (영상) |

- 영상: [task2.mp4](../../evidence/task2/board/task2.mp4)

![task2_wiring](<../../evidence/task2/board/task2_wiring.jpg>)

## 참고문헌

[1] 이해리, "STM32 실습 매뉴얼(STM32_0 · LED와 버튼, FPGA 추가 실습)" 및 "STM32 실습 안내", 서울시립대학교 전자전기컴퓨터설계실험Ⅱ, GitHub Glaysia/ece2_474 v1.1.0, 2026.

[2] D. M. Harris and S. L. Harris, *Digital Design and Computer Architecture: ARM Edition*, Morgan Kaufmann, 2015. ISBN 978-0-12-800056-4.
