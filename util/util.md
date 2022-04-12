## Utility Functions

### WrapInc

n 을 기준으로 한 modular increment (n이 2의 거듭제곱 꼴이면 bitmasking을 이용하여 더 효율적으로 구현함.)

- WrapInc(0, 5) = 1
- WrapInc(1, 5) = 2
- WrapInc(2, 5) = 3
- WrapInc(3, 5) = 4
- WrapInc(4, 5) = 0

### WrapDec

n 을 기준으로 한 modular decrement (n이 2의 거듭제곱 꼴이면 bitmasking을 이용하여 더 효율적으로 구현함.)

- WrapInc(0, 5) = 4
- WrapInc(1, 5) = 0
- WrapInc(2, 5) = 1
- WrapInc(3, 5) = 2
- WrapInc(4, 5) = 3

### MaskLower

Set all bits at or below the highest order '1'.

- `0010` -> `0011`

### MaskUpper

Set all bits at or above the lowest order '1'.

- `0010` -> `1110`

