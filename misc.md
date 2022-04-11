## Misc informations on RISC-V Boom

### Terminology

- PTW: Page Table Walker
- TLB: Translation Look-aside Buffer (Virtual Address를 Physical Address로 변환)
- CSR
- LSU: Load/Store Unit
- I$: Instruction Cache
- D$: Data Cache
- darb: 
- dcshim: 

### Rocket Chip

[reference](https://chipyard.readthedocs.io/en/dev/Generators/Rocket-Chip.html)

#### Tiles

Tile: 프로세서가 있는 부분

- Rocket core: 프로세서
- L1 I$: L1 Instruction 캐시
- L1 D$: L1 Data 캐시
- PTW: Page Table Walker
- Tile Bus: 버스

### What is LazyModule?

- [source](https://github.com/chipsalliance/rocket-chip/blob/master/src/main/scala/diplomacy/LazyModule.scala)

- Lazy하게 module을 정의하는 것? (실제로 circuit에서 모듈을 instantiation 해야 정의하는 것?)

