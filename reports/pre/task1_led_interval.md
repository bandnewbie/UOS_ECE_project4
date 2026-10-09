# 실험 전 레포트: STM32_0_과제1 · 버튼으로 LED 간격 변경

작성자: 박건우 (2025440050) / 작성일: 2026-10-09 / 소스 커밋: [65c0e73](https://github.com/bandnewbie/UOS_ECE_project4/commit/65c0e732cf25f745889f9103801a15bdc25849e7) / 보드: NUCLEO-G474RE / 제공 프로젝트: ece2_474 v1.1.0 / 도구: VS Code + STM32CubeIDE for Visual Studio Code, gnu-tools-for-stm32 14.3.1

## 목적과 예상 동작

제공 예제 1(1000 ms마다 PA5 상태 변경)과 예제 2(PC13 버튼을 누른 순간 LED 변경)를 합치고 간격 변수 `interval_ms` 하나를 추가한다 [1]. 버튼을 누를 때마다 내장 LED(PA5)의 상태 변경 간격이 1 → 2 → 4 → 8 → 1초로 바뀐다. 버튼을 계속 누르고 있어도 한 번만 바뀌고, 누르지 않아도 선택한 간격으로 계속 깜빡인다.

| 누른 횟수 | 간격 | 켜짐+꺼짐 주기 |
|---|---|---|
| 0 (시작) | 1초 | 2초 |
| 1 | 2초 | 4초 |
| 2 | 4초 | 8초 |
| 3 | 8초 | 16초 |
| 4 | 1초 | 2초 |

## 소스

- 작성 파일: [ece2_474_routine.c](../../stm32_lab/Core/Src/ece2_474_routine.c) (`polling_routine`), 보관본 [과제1_ece2_474_routine.c](../../stm32_0_tasks/과제1_ece2_474_routine.c)
- `ece2_474_init()`: 빈 상태 (타이머·PWM·UART 시작 없음) [1]
- 눌림 검출: `current == SET && previous == RESET`, 200 ms 이내 재입력 무시 [1]
- 간격 변경: `interval_ms = (interval_ms >= 8000U) ? 1000U : interval_ms * 2U;`
- 점멸: `now_ms - last_ms >= interval_ms`일 때 `led_state` 반전 후 `HAL_GPIO_WritePin`

## 사전 확인

VS Code CMake Debug 구성으로 빌드가 경고 없이 성공(종료 코드 0)했다. 처음에는 Windows 사용자 이름이 한글이라 링크 단계에서 임시 파일 생성과 `liblto_plugin.dll` 로드에 실패했고, TEMP·TMP를 `C:\Temp`로 바꾸고 Windows UTF-8 설정을 켠 뒤 build 폴더를 지우고 다시 빌드해 해결했다.

## 보드 실험 계획

Build → F5 → main에서 멈추면 F5를 한 번 더 눌러 실행한다. 1초 간격 점멸, 누를 때마다 2 → 4 → 8 → 1초 변경, 누르고 있을 때 한 번만 변경되는지 확인하고 영상으로 기록한다 [1]. 영상은 `evidence/task1/board/`에 넣는다.

## 참고문헌

[1] 이해리, "STM32 실습 매뉴얼(STM32_0 · LED와 버튼, FPGA 추가 실습)" 및 "STM32 실습 안내", 서울시립대학교 전자전기컴퓨터설계실험Ⅱ, GitHub Glaysia/ece2_474 v1.1.0, 2026.

[2] D. M. Harris and S. L. Harris, *Digital Design and Computer Architecture: ARM Edition*, Morgan Kaufmann, 2015. ISBN 978-0-12-800056-4.
