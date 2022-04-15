## Fetch Buffer

Takes a FetchBundle and converts into a vector of MicroOps.

Buffer to hold fetched packets and convert them into a vector of MicroOps to give the Decode stage

#### FetchBufferResp

Frontend 에서 Decode stage 로 넘겨주는 데이터

- uops: `Vec(coreWidth, Valid(new MicroOp()))` `coreWidth` 개의 Uop 들로 이루어져 있음.

### IO

Fetch Buffer is following Valid/Ready protocol.

- enq: `Flipped(Decoupled(new FetchBundle()))` Enqueue port
- deq: `new DecoupledIO(new FetchBufferResp())` Dequeue port
- clear: `Input(Bool())` Pipeline이 Redirect되었는지의 여부. 만약 Redirect되었다면 Fetch Buffer를 초기화한다.

### Logic

1. Convert FetchPacket into a vector of MicroOps
2. Generate one-hot write indices
3. Write MicroOps into the RAM
4. Dequeue uops
5. Update state

#### How head and tail works

Fetch Buffer is a circular buffer with head and tail.

- head: `UInt(numRows.W)` index points to the next dequeue index
- tail: `UInt(numEntries.W)` index points to the next enqueue index (`numEntries = numRows * coreWidth`)
- head와 tail의 길이가 다른 이유: head는 항상 `coreWidth` 의 배수만큼 instruction fetch를 한다?

- head and tail indexes are represented as one-hot index.
  - `0001` -> `0010` -> `0100` -> `1000` -> `0001` -> ...
- It uses `inc` and `rotateLeft` to increase indexes

#### When it sets `io.enq.ready` bit high

- `do_enq = !(at_head && maybe_full || might_hit_head)`
- at_head: tail index가 head index를 가리키고 있는지의 여부
- maybe_full: buffer의 entry가 모두 찰 가능성이 있는가?
- might_hit_head: 다음 cycle에 1~fetchWidth 개만큼 fetch했을 때 tail이 head가 될 수 있는지를 파악

> Chisel-style (explicitly set ready signal): 자유도가 높음, 벡터화가 용이함
>
> Shakeflow-style (combinator based ready signal): Modular한 표현 가능

#### Convert FetchPacket into a vector of MicroOps

- in_mask: `Vec(fetchWidth, Bool())` 들어오는 uop의 validity
- in_uops: `Vec(fetchWidth, new MicroOp())` 들어오는 uop (최대 fetchWidth개)

