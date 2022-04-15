## BoomFrontend

- Frontend: Boom 에서 Fetch + Branch Prediction 을 담당하는 부분 (Fetches from the i-cache)
- 여러 Pipeline stages 로 이루어져 있다. (F0, ..., F5)

### Pipelines

#### F0

- Select next PC
  - s1_valid && !s1_tlb_miss => f1_predicted_target
  - (s2_valid && !icache.io.resp.valid) || (s2_valid && icache.io.resp.valid && !f3_ready) => s2_vpc
  - s2_valid && f3_ready && (s1_valid && (s1_vpc != f2_predicted_target || f2_correct_f1_ghist)) || !s1_valid => f2_predicted_target
  - ...

- NextPC Select, Send request to ICache
- ICache, BPD 에 Request 를 보냄.
- `vpc`: Virtual PC Address

#### F1

- ICache Access, Translate VPC
- TLB 에 Request 를 보내고 Response 를 받음.
- `ppc`: Physical PC Address

#### F2

- ICache Response 를 받음. (Instruction return)

#### F3

- Enqueue to Fetch Buffer

#### F4

- Redirect from BPD

#### F5

- To Core (`exu/core.scala`)

### BoomFrontendBundle

### HasBoomFrontendParameters

Parameters to manage a L1 Banked ICache

- bankAlign: 
- nextFetch: 

