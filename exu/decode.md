## Decode Stage

- Take instructions from Fetch Buffer
- Decode the instruction
- Allocate the necessary resources as required by each instruction
- Combinational Logic (Pure function of input signals)

### IO

- enq: `Input(new MicroOp())` 들어오는 Uop
- deq: `Output(new MicroOp())` 나가는 Uop
- status, csr_decode, interrupt, interrupt_cause: From CSRFile (무엇인지 잘 모르겠다.)

### BranchDecodeSignals

- sfb_offset: Is this branch a short forwards jump?
- shadowable: Is this instruction allowed to be inside a sfb?

### DecodeUnit

- decode_table: `Array[(BitPat, List[BitPat])]` Decode table

### BranchDecodeSignals

- 

### BranchDecode

IO

- inst: `Input(UInt(32.W))` Instruction
- pc: `Input(UInt(vaddrBitsExtended.W))` PC Address
- out: `Output(new BranchDecodeSignals)` Branch Decode Result
