# Sequential Circuits
                      [ 컴퓨터회로 기말고사 범위 ]

* 순차회로 & Latch
* Flip-Flop
* Counter

---
---
# 순차회로

이전 상태의 신호와 외부 입력 신호에 따라 출력이 결정되는 회로

##  Memory

메모리에는 최소한 세가지 속성이 있어야 한다.
1. **Hold** a value
2. **Read** the value that was saved
3. **Change** the value that's saved

## SR latch

Inverter대신 NOR gate를 이용하여 S와 R input으로 Q와 Q' output을 제어할 수 있다.

 ![SRlatch](./img/SRlatch.png)

1. S = 0 and R = 0?
  - **No change**
  - Qnext = ( 0 + Q'current )' = Qcurrent
	 Q'next = ( 0 + Qcurrent )' = Q'current 
  - 따라서, Qnext = Qcurrent
  - 즉, Qcurrent에 따라 Qnext는 0 또는 1이 될 수 있다
  - 이전의 상태에 따라 동일한 입력이 다른 출력을 생성할 수 있음을 보여줌
 
2. S = 1 and R = 0?
  - **Set**
  - Q'next = ( 1 + Q'next )' = 0
    Qnext = ( 0 + 0 )' = 1
  - 따라서, Q'next = 0이고, Qnext = 1
  - 즉, SRlatch를 1로 설정하라는 것을 의미 

 3. S = 0 and R = 1?
   - **Reset**
   - Qnext = ( 1 + Q'current )' = 0
     Q'next = ( 0 + 0 )' = 1
   - 따라서, Qnext = 0이고 Q'next = 1
   - 즉, SRlatch를 0으로 재설정하라는 것을 의미
  
 4. S = 1 and R = 1?
   - **Avoid** Don't ever set SR=11
   - Qnext와 Q'next 모두 0 또는 1이 된다. 이는 Q와 Q'가 invert 관계가 아님
   - 무한 루프가 될 것 
 
![SRlatch상태표](./img/SRlatch_stat.png)
 
  Q와 Q '의 다음 값이 입력 값 S와 R뿐 아니라 현재 값에도 의존한다는 것을 보여준다.


## S'R' latch

NOR gate를 사용했던 SR latch와 달리 NAND gate를 사용하여 S'R' latch 설계.
Invert S (S')와 Invert R (R')을 input으로 한다.


## SR latch with a Control input

![SRlatch_control](./img/SR_control.png)

S'R' latch에 추가적인 NAND gate를 이용하여 S와 R, Control을 input으로 설계
Control은 Enable역할을 한다.


## D latch

![Dlatch](./img/Dlatch.png)
S'R' latch를 기반으로, 입력 D(data) 와 C(control)을 기반으로 S'와 R'을 생성한다.
 * C = 0일 때,  S '와 R'이 모두 1이므로 상태 Q는 변경되지 않는다.
 * C = 1일 때, 래치 출력 Q는 입력 D와 같습니다.


## Latch의 문제점
 * 정확한 시점에 래치를 비활성화 해야할 때와 활성화 해야할 때, 일반적으로 작업 소요 시간 및 래치 활성화 시간을 아는 것은 매우 어렵다. 
 * latch의 **타이밍 제어**하는 것이 어려움. -> Flip-Flop으로 개선

---
---
# Flip-Flop

대형 회로의 latch 타이밍 제어가 어려운 문제를 해결하기 위해 사용한다.
Clock과 Flip-Flop을 이용하여 문제 해결.
**Clock**은 Memory에 언제 써야하는지 알려주는 기능
**Flip-Flop**은 정확하게 정의된 시간에 메모리를 빠르게 쓸 수 있게 하는 기능
즉, 클럭과 플립플롭을 사용하여 타이밍 문제를 해결할 수 있다.

* ALU가 래치의 내용을 읽고 연산 중에는 래치를 비활성화 시켜 새로운 값을 읽지 않도록 한다.
* ALU가 연산동작을 끝내면 래치를 활성화 하고, 업데이트 된 값을 저장하도록 한다. 
* ALU가 새로운 값을 읽고 연산결과를 생성하기 전에 다시 신속하게 래치를 비횔성화 해야한다


## Clock

