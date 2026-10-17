# 실험 후 레포트: STM32_0_과제1 · 버튼으로 LED 간격 변경

작성자: 박건우 (2025440050) / 실험일: 2026-10-12 / 제출 태그: `lab4-post` / 수행 PC: 조원 노트북(SangHyeok), 빌드 확인은 본인 노트북 / 보드: NUCLEO-G474RE / 도구: VS Code + STM32CubeIDE for Visual Studio Code, gnu-tools-for-stm32 14.3.1

## 설계

제공 예제 1(1초 점멸)과 예제 2(버튼 눌림 검출)를 합치고 간격 변수 `interval_ms`를 추가했다 [1]. 눌림(LOW → HIGH, 200 ms 이내 재입력 무시)마다 간격이 1 → 2 → 4 → 8 → 1초로 바뀐다.

- 코드: [과제1_ece2_474_routine.c](../../stm32_0_tasks/과제1_ece2_474_routine.c)
- 보드 실행본(조원 노트북, 같은 사양): [조원노트북_실행본_ece2_474_routine.c](../../stm32_0_tasks/조원노트북_실행본_ece2_474_routine.c) — 간격 배열 `{1000, 2000, 4000, 8000}`과 `HAL_GPIO_TogglePin` 사용

## 빌드

CMake Debug: `Build finished with exit code 0`, RAM 2,664 B (2.03 %), FLASH 25,796 B (4.92 %)

## 보드 확인

| 확인 항목 | 예상 | 실측 |
|---|---|---|
| 버튼 안 누름 | 1초 간격 점멸 | 일치 (영상) |
| 1·2·3번 누름 | 2 → 4 → 8초 | 일치 (영상) |
| 4번 누름 | 다시 1초 | 일치 (영상) |
| 길게 누름 | 한 단계만 변경 | 일치 (영상) |

- 영상: [task1.mp4](../../evidence/task1/board/task1.mp4)

![task1_board](<../../evidence/task1/board/task1_board.jpg>)

## 참고문헌

[1] 이해리, "STM32 실습 매뉴얼(STM32_0 · LED와 버튼, FPGA 추가 실습)" 및 "STM32 실습 안내", 서울시립대학교 전자전기컴퓨터설계실험Ⅱ, GitHub Glaysia/ece2_474 v1.1.0, 2026.

[2] D. M. Harris and S. L. Harris, *Digital Design and Computer Architecture: ARM Edition*, Morgan Kaufmann, 2015. ISBN 978-0-12-800056-4.
