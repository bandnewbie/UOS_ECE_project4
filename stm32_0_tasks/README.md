# STM32_0 과제 코드 보관

- `과제1_ece2_474_routine.c`: 내장 LED(PA5), 버튼(PC13)으로 간격 1→2→4→8→1초
- `과제2_ece2_474_routine.c`: 같은 동작을 외부 LED(PB0 → 저항 330 Ω~1 kΩ → LED + / LED - → GND)로

두 파일의 차이는 `TASK_LED_GPIO_Port`, `TASK_LED_Pin` 두 줄뿐이다.
실행할 과제의 파일 내용을 `stm32_lab/Core/Src/ece2_474_routine.c`에 덮어쓰고 Build → 디버깅 종료 → F5로 다시 다운로드한다.
현재 `stm32_lab`에는 과제1 코드가 들어 있다.
