## RenameBusyTable

Tracks the readiness status of each physical register. If all physical operands are ready, the instruction will be ready to be issued.

- pregSz: log2Ceil(numPregs), **P**hysical **Reg**ister Size

### IO

- ren_uops: `Input(Vec(plWidth, new MicroOp))` 들어오는 최대 plWidth 개의 Uop들
- busy_resps: `Output(Vec(plWidth, new BusyResp))` 각 Uop 에 대한 prs1, prs2, prs3 의 readiness
- rebusy_reqs: `Input(Vec(plWidth, Bool()))`

#### How Busy Table implemented?

- busy_table: `UInt(numPregs.W)` numPregs 크기의 bit-vector 로 표현

