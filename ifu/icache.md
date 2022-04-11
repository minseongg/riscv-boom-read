## ICache

- Instruction Cache

### IO: ICacheBundle

IO signals for interacting with the ICache

- req: `Flipped(Decoupled(new ICacheReq))` ICache 에 보내는 Request
- s1_paddr: `Input(UInt(paddrBits.W))` Physical Address of PC (VPC Translation 때문에 한 사이클 Delay?)
- s1_kill: `Input(Bool())` s1 이 kill 되었는가?
- s2_kill: `Input(Bool())` s2 이 kill 되었는가?
- s2_prefetch: `Input(Bool())` I$ 가 miss 일때 다음 line 을 prefetch 해야 하는가?
- resp: `Valid(new ICacheResp(outer))` ICache 에서 나가는 Response
- invalidate: `Input(Bool())`

### ICacheModule

ICache 에서 lazy하게 이 모듈을 정의한다. 실질적인 구현은 여기 있음.

