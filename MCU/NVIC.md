인터럽트의 우선순위를 관리하는 기능

- 프로세서 코어 내부에 있음
- 인터럽트 스택킹, 언스택킹을 관리하고, 중첩을 가능하게 함
- 벡터 테이블을 기반으로 ISR를 호출함

### 주요 레지스터

- **ISER** (Interrupt Set-Enable Registers) — IRQ 활성화
- **ICER** (Interrupt Clear-Enable Registers) — IRQ 비활성화
- **ISPR** (Interrupt Set-Pending) / **ICPR** (Clear-Pending) — pending 상태 조작
- **IABR** (Interrupt Active Bit Registers) — 현재 active 여부 확인
- **IPR** (Interrupt Priority Registers) — 우선순위 설정

### 예외

리셋, NMI, SVC, Systick 등은 코어가 직접 관리함

외부 주변장치의 인터럽트는 모두 얘가 다 함

- SysTick
    
    인터럽트 발생시키는 타이머
    
    | `SYST_CSR` (Control and Status Register) | SysTick 타이머를 켜거나 끄고, 인터럽트를 쓸지 설정함 |
    | --- | --- |
    | `SYST_RVR` (Reload Value Register) | 타이머가 얼마만큼 셀지 정하는 값 (주기 설정) |
    | `SYST_CVR` (Current Value Register) | 현재 카운트 값 |
    | `SYST_CALIB` (Calibration Register) | 캘리브레이션 값 (시스템 클록 기준 주기 보정용) |

### 알아두면 좋은 것들

`void TIM2_IRQHandler(void)` 벡터를 호출할 때 이 함수를 사용함

`NVIC_EnableIRQ()` 실제 주소 비트를 접근할 수 있게 하는 API도 제공함
