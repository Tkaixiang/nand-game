# Nand Game Adventures

## 1. `NAND` (opposite of `AND`)

- Only returns **Negative** (`0`) if **both signals (`AND`)** are **positive**

| Input A | Input B | Output |
| ------- | ------- | ------ |
| 0       | 0       | 1      |
| 0       | 1       | 1      |
| 1       | 0       | 1      |
| 1       | 1       | 0      |

![](assets/1.png)

- _Note:_ The "spinny magnetic field" is indeed a **magnetic field** that attracts when powered

## 2. `NOT` (Inverter)

| Input | Output |
| ----- | ------ |
| 0     | 1      |
| 1     | 0      |

![](assets/2.png)

## 3. `AND` (opposite of `NAND`)

- Only returns **Positive** (`1`) if **both signals (`AND`)** are **positive**

| Input A | Input B | Output |
| ------- | ------- | ------ |
| 0       | 0       | 0      |
| 0       | 1       | 0      |
| 1       | 0       | 0      |
| 1       | 1       | 1      |

![](assets/3.png)

## 4. `OR`

- Returns **Positive** (`1`) if **either signals (`OR`)** are **positive**

| Input A | Input B | Output |
| ------- | ------- | ------ |
| 0       | 0       | 0      |
| 0       | 1       | 1      |
| 1       | 0       | 1      |
| 1       | 1       | 1      |

- What we need is a _nullify_ effect (does nothing) since the original power switches already provide this result
