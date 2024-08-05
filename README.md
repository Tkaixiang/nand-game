# Nand Game Adventures

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

<img src="assets/5.png" width="350"/>
