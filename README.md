# Nand Game Adventures

- `save.json` contains the save for `nandgame`

## 1. `NAND` (opposite of `AND`)

- Only returns **Negative** (`0`) if **both signals (`AND`)** are **positive**

| Input A | Input B | Output |
| ------- | ------- | ------ |
| 0       | 0       | 1      |
| 0       | 1       | 1      |
| 1       | 0       | 1      |
| 1       | 1       | 0      |

<img src="assets/1.png" width="350"/>

- _Note:_ The "spinny magnetic field" is indeed a **magnetic field** that attracts when powered

## 2. `NOT` (Inverter)

| Input | Output |
| ----- | ------ |
| 0     | 1      |
| 1     | 0      |

<img src="assets/2.png" width="350"/>

## 3. `AND` (opposite of `NAND`)

- Only returns **Positive** (`1`) if **both signals (`AND`)** are **positive**

| Input A | Input B | Output |
| ------- | ------- | ------ |
| 0       | 0       | 0      |
| 0       | 1       | 0      |
| 1       | 0       | 0      |
| 1       | 1       | 1      |

<img src="assets/3.png" width="350"/>

## 4. `OR`

- Returns **Positive** (`1`) if **either signals (`OR`)** are **positive**

| Input A | Input B | Output |
| ------- | ------- | ------ |
| 0       | 0       | 0      |
| 0       | 1       | 1      |
| 1       | 0       | 1      |
| 1       | 1       | 1      |

- We **invert** the inputs into `NAND`

<img src="assets/4.png" width="350"/>

## 5. `XOR` (Exclusive OR)

- Returns **Positive** (`1`) when the inputs are **different**

| Input A | Input B | Output |
| ------- | ------- | ------ |
| 0       | 0       | 0      |
| 0       | 1       | 1      |
| 1       | 0       | 1      |
| 1       | 1       | 0      |

- Sort of a "both gates must agree" to pass

### Least Components Solution

<img src="assets/5.png" width="350"/>

### Least Nand Gates Solution (wtf)

<img src="assets/5-1.png" width="350"/>

## 6. Half `Adder`

- Adds **`2` `1-bit` numbers**

| A   | B   | Sum (High) | Sum (Low) |
| --- | --- | ---------- | --------- |
| 0   | 0   | 0          | 0         |
| 0   | 1   | 1          | 0         |
| 1   | 0   | 1          | 0         |
| 1   | 1   | 0          | 1         |

<img src="assets/6.png" width="350"/>

## 6. (Full) `Adder`

- Adds **`3` `1-bit` numbers** into a **`2-bit` value**

| A   | B   | C_in | Sum (S) | Carry-out (C_out) |
| --- | --- | ---- | ------- | ----------------- |
| 0   | 0   | 0    | 0       | 0                 |
| 0   | 0   | 1    | 1       | 0                 |
| 0   | 1   | 0    | 1       | 0                 |
| 0   | 1   | 1    | 0       | 1                 |
| 1   | 0   | 0    | 1       | 0                 |
| 1   | 0   | 1    | 0       | 1                 |
| 1   | 1   | 0    | 0       | 1                 |
| 1   | 1   | 1    | 1       | 1                 |

<img src="assets/7.png" width="350"/>

- Adding the **`1-bit` numbers** together (using `add`) and handling the **high-bit** seperartely
  - will \*trigger the **output high-bit\*** either when either addition results in the **addition high-bit** being triggered.

## 6. Multi-Bit `Adder`

- Adds 2 **`2-bit` numbers** and 1 **`1-bit` carry** to form a **`3-bit` number**

<img src="assets/8-table.png" width="350"/>

<img src="assets/8.png" width="350"/>

- Combine the **`1-bit`s** to form a **`2-bit` number**
- We now have **3 `2-bits`** and **1 `1-bit`** (connect the **`1-bit`** to `s0`)
  - Sum the `2-bits` and treat the output as a **`3-bit` and `2-bit` output**

## 7. 16-Bit Increments

- Add `1` to a `16-bit Number`

<img src="assets/9.png" width="350"/>

- Simply use the **carry-bit (`1`)**

## 8. 16-Bit Substraction

- **`16-bit Unsigned Integer` range: `0 <= x <= 65536`**
- **`16-bit Signed Integer` range: `-32767 <= x <= 32767`** (because it uses half for the **negative-signs**)
  - ### <u>Two-Complement Representation:</u>
  - In **Decimal:**
    - **Negative Numbers** are represented as `65536 - Overflow`
    - _E.g 65536 - 65535 = 1 - represents `-1`_
  - In **Binary:**
    - `1111111111111110` (if `MSB`==1, it is a `-ve` number)

<img src="assets/10.png" width="350"/>

- <u>Note:</u> We need to **<u>add `1`</u>** due to how the 2-complement **inverting** works:
  - When **inverting** `1111111111111110`, we get `0000000000000001`
  - Afterwards, we add `1` and get `0000000000000010` (`2`)
    - _This is part of a "Zero Balance"_
  - Taking into account the **sign (`1`)**, it is a `-ve` and we get `-2`
  - $\therefore$ _We need to "balance it out" by adding `1`_ afterwards

## 9. Equal to Zero

- Output `1` only if all inputs are `0`

<img src="assets/11.png" width="350"/>

- _(is this even optimal?)_

## 10. Equal to Zero

- Output `1` if the **MSB (`15th-bit`)** is `1` (indicates `-ve` as noted in `8.`)

<img src="assets/12.png" width="350"/>

## 11. Selector

- The `s` (`Select`) bit selects which **<u>input</u>** to select.
  - If `s==0`, select `d0`, if `s==1`, select `d1`

| S   | D0  | D1  | Out |
| --- | --- | --- | --- |
| 0   | 0   | 0   | 0   |
| 0   | 0   | 1   | 0   |
| 0   | 1   | 0   | 1   |
| 0   | 1   | 1   | 1   |
| 1   | 0   | 0   | 0   |
| 1   | 0   | 1   | 1   |
| 1   | 1   | 0   | 0   |
| 1   | 1   | 1   | 1   |

<img src="assets/13.png" width="350"/>

- Use 2 `AND` to conditionally select, but invert the `s==0`

## 12. Switch

- The `s` (`Switch`) bit selects which **<u>output</u>** to output to.
  - If `s==0`, output to `c0`, if `s==1`, output to `c1`

| S   | In  | D0  | D1  |
| --- | --- | --- | --- |
| 0   | 0   | 0   | 0   |
| 0   | 1   | 1   | 0   |
| 1   | 0   | 0   | 0   |
| 1   | 1   | 0   | 1   |

<img src="assets/14.png" width="350"/>

## 13. Logic Unit

- Select between 4 **Logic** Operations depending on `op0` and `op1`

| op1 | op0 | Operation |
| --- | --- | --------- |
| 0   | 0   | X AND Y   |
| 0   | 1   | X OR Y    |
| 1   | 0   | X XOR Y   |
| 1   | 1   | Invert X  |

<img src="assets/15.png" width="350"/>

- _(optimal is 7 components, but this uses 8)_

## 14. Arithmetic Unit

- Select between 4 **Arithmetic** Operations depending on `op0` and `op1`

| op1 | op0 | Operation |
| --- | --- | --------- |
| 0   | 0   | X + Y     |
| 1   | 0   | X - Y     |
| 0   | 1   | X + 1     |
| 1   | 1   | X - 1     |

<img src="assets/16.png" width="350"/>

## 15. Arithmetic Logic Unit (ALU)

- Select between 9 **Arithmetic** Operations depending on `op0`, `op1` and `u`
- Also provides 2 additional **flags**:
  - When `sw` flag is `1`, `X` and `Y` are **swapped**
  - When `zx` flag is `1`, **left operand** is set to `0`

| u   | op1 | op0 | Operation |
| --- | --- | --- | --------- |
| 0   | 0   | 0   | X AND Y   |
| 0   | 0   | 1   | X OR Y    |
| 0   | 1   | 0   | X XOR Y   |
| 0   | 1   | 1   | Invert X  |
| 1   | 0   | 0   | X + Y     |
| 1   | 1   | 0   | X - Y     |
| 1   | 0   | 1   | X + 1     |
| 1   | 1   | 1   | X - 1     |

| zx  | sw  | Effective Operation |
| --- | --- | ------------------- |
| 0   | 0   | X - Y               |
| 0   | 1   | Y - X               |
| 1   | 0   | 0 - Y               |
| 1   | 1   | 0 - X               |

<img src="assets/17.png" width="350"/>

## 16. Condition

- Given 3 flags below which each represent a condition:

| Flag | Condition         |
| ---- | ----------------- |
| lt   | Less than zero    |
| eq   | Equal to zero     |
| gt   | Greater than zero |

- We want to output when 1:

| lt  | eq  | gt  | Output 1 When |
| --- | --- | --- | ------------- |
| 0   | 0   | 0   | Never         |
| 0   | 0   | 1   | X > 0         |
| 0   | 1   | 0   | X = 0         |
| 0   | 1   | 1   | X ≥ 0         |
| 1   | 0   | 0   | X < 0         |
| 1   | 0   | 1   | X ≠ 0         |
| 1   | 1   | 0   | X ≤ 0         |
| 1   | 1   | 1   | Always        |

<img src="assets/18.png" width="350"/>

## 17. SR Latch (Set/Reset Latch)

- `s=1` (**set**) sets output to `1`
- `r=1` (**reset**) sets output to `0`

- When both `s=1,r=1`, the output takes the **<u>Previous Output</u>**

| s   | r   | Output          |
| --- | --- | --------------- |
| 1   | 0   | 1               |
| 0   | 1   | 0               |
| 1   | 1   | Previous output |
| 0   | 0   | Not used        |

<img src="assets/19.png" width="350"/>

- Behaviour when we activate `r` then `s` (output is `0`)
  - When `r` is activated, `Left-Nand` `b=1` is set which causes `Left-Nand` to output `0` and set `Right-Nand` `a=0`
  - When `s` is activated, it sets `Right-Nand` `b=1`. But this is not enough to change anything since `Right-Nand`'s `a=0` already

<img src="assets/19-1.png" width="350"/>

- Behaviour when we activate `s` then `r` (output is `1`)
  - When `s` is activated, `Right-Nand` `b=1` is set which causes `Right-Nand` to output `0` and set `Left-Nand`'s `a=0`
  - When `r` is activated, it sets `Left-Nand`'s `b=1`. But this is not enough to change anything since `Left-Nand`'s `a=0` already.
