# Computer System Architecture – CPU Sim Lab

## CPU Sim Practical Assignment

This repository contains my Computer System Architecture (CSA) CPU Sim Lab practical assignments.

The practicals are implemented and simulated using **CPU Sim** based on **Mano's Basic Computer Architecture**.

---

## Student Information

| Details | Information |
|---|---|
| Name | Your Name |
| Roll No. | Your Roll Number |
| Course | B.Sc. (Hons.) Computer Science |
| Semester | Semester 1 |
| College | Ramanujan College |
| University | University of Delhi |

---

# Index of Practicals

| S. No. | Practical |
|---:|---|
| 1 | Create a machine based on Basic Computer Architecture |
| 2 | Create the Fetch Routine of the Instruction Cycle |
| 3 | Addition of Two Numbers |
| 4 | Subtraction of Two Numbers |
| 5 | Logical Operations |
| 6 | Memory Reference Instructions |
| 7 | Register Reference Instructions – CLA, CMA, CME, HLT |
| 8 | Register Reference Instructions – INC, SPA, SNA, SZE |
| 9 | Rotate Instructions – CIR and CIL |
| 10 | Sum of Integers Until a Negative Number |
| 11 | Sum of Integers Until Zero |

---

# Practical 1 – Basic Computer Architecture

## Aim

To create a machine based on **Mano's Basic Computer Architecture** using CPU Sim.

## Description

The Basic Computer architecture was created and configured in CPU Sim.

The machine consists of registers, memory, ALU and other components required to execute instructions.

## Software Used

- CPU Sim
- Mano's Basic Computer Architecture

## Result

The Basic Computer machine was successfully created and simulated in CPU Sim.

---

# Practical 2 – Fetch Routine

## Aim

To create and simulate the **Fetch Routine of the Instruction Cycle**.

## Description

The fetch cycle is responsible for obtaining an instruction from memory and loading it into the Instruction Register.

The basic operations involved in the fetch cycle include:

1. Transfer the contents of the Program Counter to the Address Register.
2. Read the instruction from memory.
3. Transfer the instruction to the Instruction Register.
4. Increment the Program Counter.

## Result

The Fetch Routine was successfully implemented and simulated in CPU Sim.

---

# Practical 3 – ADD Operation

## Aim

To write an assembly program to add two user-entered numbers.

## CPU Sim Code

```asm
INP
STA A
INP
ADD A
OUT
HLT

A:   .data 1 0
SUM: .data 1 0
```

## Explanation

- `INP` – Takes input from the user.
- `STA A` – Stores the first number in memory location A.
- `INP` – Takes the second number.
- `ADD A` – Adds the first number to the second number.
- `OUT` – Displays the result.
- `HLT` – Stops execution.

## Sample Output

```text
Enter Inputs, the first of which must be an Integer: 5
Enter Inputs, the first of which must be an Integer: 3
Output: 8
```

## Result

The program successfully adds two numbers and displays their sum.

---

# Practical 4 – SUBTRACT Operation

## Aim

To write an assembly program to subtract two user-entered numbers.

## CPU Sim Code

```asm
INP
STA A
INP
CMA
INC
ADD A
STA DIFF
OUT
HLT

A:    .data 1 0
DIFF: .data 1 0
```

## Explanation

The subtraction is performed using the **two's complement method**.

- `CMA` – Complements the accumulator.
- `INC` – Adds 1 to obtain the two's complement.
- `ADD A` – Adds the first number.
- `OUT` – Displays the result.

## Sample Output

```text
Enter Inputs, the first of which must be an Integer: 9
Enter Inputs, the first of which must be an Integer: 3
Output: 6
```

## Result

The program successfully performs subtraction using the Basic Computer instructions.

---

# Practical 5 – Logical Operations

## Aim

To implement logical operations using CPU Sim.

## Logical Operations

The following logical operations were implemented:

- AND
- OR
- NOT
- XOR
- NOR
- NAND

## CPU Sim Code

```asm
; AND

LDA A
AND B
STA RAND
OUT


; OR

LDA A
CMA
AND B
CMA
STA ROR
OUT


; NOT A

LDA A
CMA
STA NA
OUT


; NOT B

LDA B
CMA
STA NB
OUT


; XOR = (A + B) . (A . B)'

LDA RAND
CMA
STA NRAND
LDA ROR
AND NRAND
STA RXOR
OUT


; NOR = (A + B)'

LDA ROR
CMA
STA RNOR
OUT


; NAND = (A . B)'

LDA RAND
CMA
STA RNAND
OUT

HLT

A:      .data 1 0
B:      .data 1 0
NA:     .data 1 0
NB:     .data 1 0
RAND:   .data 1 0
ROR:    .data 1 0
RXOR:   .data 1 0
RNOR:   .data 1 0
RNAND:  .data 1 0
```

## Result

The required logical operations were successfully implemented and simulated in CPU Sim.

---

# Practical 6 – Memory Reference Instructions

## Aim

To implement memory-reference instructions using CPU Sim.

## Instructions Used

- LDA – Load Accumulator
- ADD – Add
- STA – Store Accumulator
- ISZ – Increment and Skip if Zero
- BUN – Branch Unconditionally

## CPU Sim Code

```asm
LOOP: LDA PROD
      ADD X
      STA PROD
      ISZ CTR
      BUN LOOP
      LDA PROD
      HLT

X:    .data 1 5
CTR:  .data 1 -3
PROD: .data 1 0
```

## Explanation

The program repeatedly adds the value stored in `X` to `PROD`.

`CTR` controls the number of repetitions.

## Result

The memory-reference instructions were successfully implemented and executed.

---

# Practical 7 – CLA, CMA, CME and HLT

## Aim

To implement register-reference instructions:

- CLA
- CMA
- CME
- HLT

## CPU Sim Code

```asm
LDA NUM
CLA
CMA
CME
HLT

NUM: .data 1 25
```

## Explanation

- `LDA` – Loads the value into AC.
- `CLA` – Clears the accumulator.
- `CMA` – Complements the accumulator.
- `CME` – Complements the E flip-flop.
- `HLT` – Stops execution.

## Result

The register-reference instructions were successfully implemented and simulated.

---

# Practical 8 – INC, SPA, SNA and SZE

## Aim

To implement conditional register-reference instructions.

## Instructions Used

- INC – Increment AC
- SPA – Skip if AC is positive
- SNA – Skip if AC is negative
- SZE – Skip if E is zero

## CPU Sim Code

```asm
LDA NUM
INC
SNA
HLT
INC
SPA
HLT
SZE
HLT
INC
HLT

NUM: .data 1 -2
```

## Result

The required register-reference and skip instructions were successfully implemented and simulated.

---

# Practical 9 – CIR and CIL

## Aim

To implement the rotate instructions:

- CIR – Circulate Right
- CIL – Circulate Left

## CPU Sim Code

```asm
LDA NUM
CIR
CIR
CIL
CIL
HLT

NUM: .data 1 9
```

## Explanation

- `CIR` rotates the accumulator and E bit to the right.
- `CIL` rotates the accumulator and E bit to the left.

## Result

The CIR and CIL instructions were successfully implemented and simulated.

---

# Practical 10 – Sum Until Negative

## Aim

To write a program that accepts integers and calculates their sum until a negative number is entered.

## CPU Sim Code

```asm
LOOP: INP
      SPA
      BUN DONE
      ADD SUM
      STA SUM
      BUN LOOP

DONE: LDA SUM
      OUT
      HLT

SUM:  .data 1 0
```

## Explanation

The program:

1. Takes an integer as input.
2. Checks whether it is positive.
3. If it is positive, it adds it to the running total.
4. If a negative number is entered, the program stops accepting numbers.
5. The final sum is displayed.

## Sample Input

```text
4
10
6
0
-3
```

## Sample Output

```text
Output: 20
```

## Result

The program successfully calculates the sum of the entered integers until a negative number is encountered.

---

# Practical 11 – Sum Until Zero

## Aim

To write a program that accepts integers and calculates their sum until zero is entered.

## CPU Sim Code

```asm
LOOP: INP
      SZA
      BUN ADDIT
      BUN DONE

ADDIT: ADD SUM
       STA SUM
       BUN LOOP

DONE: LDA SUM
      OUT
      HLT

SUM: .data 1 0
```

## Explanation

The program:

1. Accepts an integer as input.
2. Checks whether the input is zero.
3. If the input is not zero, it is added to the running total.
4. If zero is entered, the loop terminates.
5. The final sum is displayed.

## Sample Input

```text
8
12
-5
0
```

## Sample Output

```text
Output: 15
```

## Result

The program successfully calculates the sum of integers until zero is entered.

---

# Software Used

- CPU Sim
- Java
- Mano's Basic Computer Architecture

---

# CPU Sim Instructions Covered

| Category | Instructions |
|---|---|
| Input/Output | INP, OUT |
| Memory Reference | LDA, STA, ADD, BUN, ISZ |
| Register Reference | CLA, CMA, CME, INC, HLT |
| Skip Instructions | SPA, SNA, SZE, SZA |
| Rotate Instructions | CIR, CIL |
| Logical Operations | AND, OR, NOT, XOR, NOR, NAND |

---

# Repository Structure

```text
CSA-CPU-Sim-Lab-Practical/
│
├── README.md
│
├── Practical-01/
├── Practical-02/
├── Practical-03-ADD/
├── Practical-04-SUBTRACT/
├── Practical-05-LOGICAL-OPERATIONS/
├── Practical-06-MEMORY-REFERENCE/
├── Practical-07-REGISTER-REFERENCE/
├── Practical-08-CONDITIONAL-INSTRUCTIONS/
├── Practical-09-CIR-CIL/
├── Practical-10-SUM-UNTIL-NEGATIVE/
└── Practical-11-SUM-UNTIL-ZERO/
```

---

# Conclusion

These practicals demonstrate the implementation and simulation of fundamental concepts of **Computer System Architecture** using CPU Sim and Mano's Basic Computer Architecture.

The practicals cover arithmetic operations, logical operations, memory-reference instructions, register-reference instructions, conditional branching, rotate operations and iterative programs.
