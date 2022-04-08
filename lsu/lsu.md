## RISC-V Out-of-Order Load/Store Unit

Load/Store Unit is made up of the following three queues:

- LAQ: Load-Address Queue
- SAQ: Store-Address Queue
- SDQ: Store-Data Queue

### LSU

#### IO

- ptw: `rocket.TLBPTWIO` Page Table Walker
- core: `LSUCoreIO` Load/Store Unit Core IO
- dmem: `LSUDMemIO` Load/Store Unit DMem IO





- ldq: `Reg(Vec(numLdqEntries, Valid(new LDQEntry)))` Load Queue
- stq: `Reg(Vec(numStqEntries, Valid(new STQEntry)))` Store Queue

- ldq_head, ldq_tail, stq_head, stq_tail: head / tail of queues
- stq_commit_head, stq_execute_head: Pointer to next store to commit / execute

#### Decode Stage

Next enqueue index

- ld_enq_idx: ldq_tail
- st_enq_idx: stq_tail

#### Execution Stage

#### Memory Stage

#### Writeback Stage

### LSUDMemIO

