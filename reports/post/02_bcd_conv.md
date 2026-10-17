# 실험 후 레포트: 02 BCD → 이진수 변환

작성자: 박건우 (2025440050) / 실험일: 2026-10-12 / 제출 태그: `lab4-post` / 수행 PC: 조원 노트북(SangHyeok) / 도구: Vivado 2026.1 / part: xc7s75fgga484-1 / 설계 Top: `bcd_conv` / 시뮬레이션 Top: `tb` / XDC: [bcd_conv.xdc](../../lab4_02_bcd_conv/constraints/bcd_conv.xdc)

## Vivado 시뮬레이션

| 도구 | 결과 | 종료 시각 |
|---|---|---|
| VS Code (Icarus Verilog, 실험 전) | `PASS BCD: 100 valid and 156 invalid inputs` | 256 ns |
| Vivado XSim | `PASS BCD: 100 valid and 156 invalid inputs` | 256 ns |

시뮬레이션 끝의 ten=f, one=f에서 bin=0x25: 15×10+15 = 165가 7비트를 넘어 37만 남고 valid=0.

![wave_vivado](<../../evidence/02/vivado/wave_vivado.png>)

## 합성·구현·비트스트림

synth_1, impl_1 완료, 비트스트림 생성. 처음 `open_hw_target`에서 `No devices detected`가 나와 연결을 다시 확인한 뒤 `bcd_conv.bit` 기록 성공.

![bitstream_done](<../../evidence/02/vivado/bitstream_done.png>)

- Tcl 로그: [tcl_console.txt](../../evidence/02/vivado/tcl_console.txt)

## 보드 확인

핀: DIP1~4 = `ten[3:0]`, DIP5~8 = `one[3:0]`, LED1 = `valid`, LED2~8 = `bin[6:0]`

| 입력 ten·one | 예상 bin | 예상 valid | 실측 |
|---|---|---|---|
| 4·2 | 010_1010 (42) | 1 | 일치 |
| 9·9 | 110_0011 (99) | 1 | 일치 |
| 0·12 | 000_1100 (12) | 0 | 일치 |

- 영상: [bcd_conv_board.mp4](../../evidence/02/board/videos/bcd_conv_board.mp4)

![bcd_conv_board](<../../evidence/02/board/photos/bcd_conv_board.jpg>)

## 비교·결론

VS Code와 Vivado의 PASS 결과가 같고, 범위 밖 입력에서 valid=0으로 구분되는 것까지 보드에서 확인했다.

## 참고문헌

[1] 이해리, "STM32 실습 매뉴얼(STM32_0 · LED와 버튼, FPGA 추가 실습)" 및 "STM32 실습 안내", 서울시립대학교 전자전기컴퓨터설계실험Ⅱ, GitHub Glaysia/ece2_474 v1.1.0, 2026.

[2] D. M. Harris and S. L. Harris, *Digital Design and Computer Architecture: ARM Edition*, Morgan Kaufmann, 2015. ISBN 978-0-12-800056-4.
