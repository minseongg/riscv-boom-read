## BoomFrontend

- Frontend: Boom 에서 Fetch + Branch Prediction 을 담당하는 부분 (Fetches from the i-cache)
- 여러 Pipeline stages 로 이루어져 있다. (F0, ..., F5)

### F0

- NextPC Select, Send request to ICache
- ICache, BPD 에 Request 를 보냄.
- `vpc`: Virtual PC Address

### F1

- ICache Access, Translate VPC
- TLB 에 Request 를 보내고 Response 를 받음.
- `ppc`: Physical PC Address

### F2

- ICache Response 를 받음.

### F3

### F4

### F5

- To Core

### BoomFrontendBundle

