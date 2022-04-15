## RenameStage

ISA (or logical) register -> Physical register

Connects the map table, free list and busy table.

Branch가 Rename stage를 지날 때, snapshot 을 저장해 놓아야 함 => misprediction이 발생했을 때 복구하기 위해

### Parameters

- plWidth: `Int` pipeline width
- numPhysRegs: `Int` number of physical registers
- numWbPorts: `Int` number of writeback ports
- float: `Boolean` is float?

### IO

- dec_uops: `Input(Vec(plWidth, new MicroOp()))` decode uops

### Pipeline

#### Rename1

- ren1_uops: `Wire(Vec(plWidth, new MicroOp))` Decode stage 에서 넘겨주는 Uops

#### Rename2

