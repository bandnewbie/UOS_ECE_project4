# 실험 후 레포트: 01 4비트 곱셈기

작성자: 박건우 (2025440050) / 실험일: 2026-10-12 / 제출 태그: `lab4-post` / 수행 PC: 조원 노트북(SangHyeok) / 도구: Vivado 2026.1 / part: xc7s75fgga484-1 / 설계 Top: `mult_4bit` / 시뮬레이션 Top: `tb` / XDC: [mult_4bit.xdc](../../lab4_01_mult_4bit/constraints/mult_4bit.xdc)

## Vivado 시뮬레이션

| 도구 | 결과 | 종료 시각 |
|---|---|---|
| VS Code (Icarus Verilog, 실험 전) | `PASS multiplier: 256 input pairs` | 256 ns |
| Vivado XSim | `PASS multiplier: 256 input pairs` | 256 ns |

![wave_vivado](<../../evidence/01/vivado/wave_vivado.png>)

## 합성·구현·비트스트림

synth_1, impl_1 완료, 비트스트림 생성. Hardware Manager로 xc7s75에 `mult_4bit.bit` 기록 (`program_hw_devices`, End of startup status: HIGH).

![bitstream_done](<../../evidence/01/vivado/bitstream_done.png>)

- Tcl 로그: [tcl_console.txt](../../evidence/01/vivado/tcl_console.txt)

## 보드 확인

핀: DIP1~4 = `a[3:0]`, DIP5~8 = `b[3:0]`, LED1~8 = `m[7:0]`

| 입력 a×b | 예상 m | 실측 |
|---|---|---|
| 3×5 | 0000_1111 (15) | 일치 |
| 15×15 | 1110_0001 (225) | 일치 |
| 0×b | 0000_0000 | 일치 |

- 영상: [mult_4bit_board.mp4](../../evidence/01/board/videos/mult_4bit_board.mp4)

![mult_4bit_board](<../../evidence/01/board/photos/mult_4bit_board.jpg>)

## 비교·결론

VS Code와 Vivado의 PASS 결과가 같고, 보드 출력도 예상값과 같았다.

## 참고문헌

[1] 이해리, "STM32 실습 매뉴얼(STM32_0 · LED와 버튼, FPGA 추가 실습)" 및 "STM32 실습 안내", 서울시립대학교 전자전기컴퓨터설계실험Ⅱ, GitHub Glaysia/ece2_474 v1.1.0, 2026.

[2] D. M. Harris and S. L. Harris, *Digital Design and Computer Architecture: ARM Edition*, Morgan Kaufmann, 2015. ISBN 978-0-12-800056-4.
