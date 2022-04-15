## BoomCore

Frontend와 나머지 부분들을 연결해주는 Top level core object

### Pipeline State Registers and Wires

#### Decode/Rename1 Stage

- dec_valids: `Wire(Vec(coreWidth, Bool()))` 한번에 `coreWidth` 개의 Uop들을 받고 decode한다.
- dec_uops: decode된 결과 Uop들
- dec_ready: 모든 decode_unit 들이 비어있을 때 high

> Pattern 1: N input - 1 Output, Ready bit high if all Valid bits high

#### When the `dec_valids` bits high?

decode stage 에서는 frontend 로부터 최대 `coreWidth` 개의 Uop 들을 전달받는다.

- `dec_valids(w)` high when these conditions are true.
  - `io.ifu.fetchpacket.valid`
  - `dec_fbundle.uops(w).valid`
  - `!dec_finished_mask(w)`

> Chisel 코드에서, 임의의 variable 이 어떤 cycle 에 바뀌는지에 대한 정보를 알기가 조금 어렵다.
>
> Shakeflow 에서는, combinator 들의 formal semantic 을 통해 cycle 에 대한 정보를 알기가 더 쉽다.



