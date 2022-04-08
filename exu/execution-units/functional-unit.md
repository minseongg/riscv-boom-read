## Functional Unit

### FUConstants

Functional Unit 을 설명하기 위한 Constants (bitmask 형태로 나타낼 수 있다.)

- FU_ALU
- FU_JMP
- FU_MEM
- FU_MUL
- FU_DIV
- FU_CSR
- FU_FPU
- FU_FDV
- FU_I2F
- FU_F2I
- FU_F2IMEM = FU_MEM | FU_F2I

### SupportedFuncUnits

Function Unit Decoder에게 어떤 Unit을 지원해야 하는지를 알려주기 위한 class

- alu: ALU
- jmp: JMP
- mem: MEM
- muld: Multiple Div
- fpu: FP
- csr: CSR Writing
- fdiv: FP Div
- ifpu: INT to FP

### FuncUnitReq

Functional Unit 으로 보내는 Request Data

- rs1_data: RS1 Register
- rs2_data: RS2 Register
- rs3_data: RS3 Register (Only used for FMA units: Floating-point Multiplication and Addition)
- pred_data: Predicate 된 값인지의 여부?
- kill: Kill everything (Flush pipeline)

### FuncUnitResp

Functional Unit 에서 나오는 Response Data

- predicated: predicate 된 instruction 에서 나온 값인지의 여부
- data: Executed Data
- fflags: 
- addr: 
- mxcpt: 
- sfence: 

### BrUpdateInfo

- b1: BrUpdateMasks, 
- b2: BrResolutionInfo, 

### ALUUnit

Functional Unit that wraps RocketChips ALU

### MemAddrCalcUnit

Functional Unit that passes in base+imm to calculate addresses, and passes store data to the LSU

### FPUUnit

Functional Unit to wrap lower level FPU

### DivUnit

Divide Functional Unit

- dataWidth: Functional Unit 으로 들어오는 Data의 크기

