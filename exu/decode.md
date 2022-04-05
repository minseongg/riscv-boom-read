# Decode Stage

- Take instructions from Fetch Buffer
- Decode the instruction
- Allocate the necessary resources as required by each instruction

### DecodeUnitIo

- enq, deq: MicroOp

### BranchDecodeSignals

- sfb_offset: Is this branch a short forwards jump?
- shadowable: Is this instruction allowed to be inside a sfb?

