## FetchTargetQueue

Queue to store the fetch PC and other relevant branch predictor signals that are inflight in the processor.

### IO

- enq: `Flipped(Decoupled(new FetchBundle()))` 매 fetch cycle마다 하나의 fetch bundle이 들어옴.
- deq: `Flipped(Valid(UInt(idx_sz.W)))` ROB에서 commit된 ftq_idx를 알려줌 => FTQ에서 제거

#### When it sets `io.enq.ready` bit high?

- `io.enq.ready := RegNext(!full || do_commit_update)`

> Shakeflow 의 Modularity 를 더 잘 살리려면:
>
> - ValidReady Channel 들의 의미들을 좀 더 명확하게 하는 것이 중요할 것 같음.
> - 그리고 combinator 들의 semantic을 명확하게 한다면 이를 조합하는 것들이 더 의미있어질 것임. (Intermediate value에 대해서도)
