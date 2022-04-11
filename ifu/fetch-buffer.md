## Fetch Buffer

Takes a FetchBundle and converts into a vector of MicroOps.

Buffer to hold fetched packets and convert them into a vector of MicroOps to give the Decode stage

### IO

- enq: `Flipped(Decoupled(new FetchBundle()))` 
- deq: `new DecoupledIO(new FetchBufferResp())` 
- clear: `Input(Bool())` Pipeline이 Redirect되었는지의 여부. 만약 Redirect되었다면 Fetch Buffer를 초기화한다.

### Logic

1. Convert FetchPacket into a vector of MicroOps
2. Generate one-hot write indices
3. Dequeue uops
4. Update state