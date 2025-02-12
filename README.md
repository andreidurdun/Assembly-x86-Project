# Conway's Game of Life and Symmetric Encryption Scheme

## Problem Statement
Conway’s Game of Life is a two-dimensional zero-player game invented by mathematician John Horton Conway in 1970. The game consists of an evolving system of cells that follow predefined rules regarding their survival, death, or birth in the next generation. This system is Turing-complete and can simulate complex computational processes.

The state of the system is determined by the collective state of its cells, which follow these rules:
1. **Underpopulation:** Any live cell with fewer than two live neighbors dies in the next generation.
2. **Survival:** Any live cell with two or three live neighbors survives to the next generation.
3. **Overpopulation:** Any live cell with more than three live neighbors dies in the next generation.
4. **Reproduction:** Any dead cell with exactly three live neighbors becomes a live cell in the next generation.
5. **Dead Cell Continuation:** Any other dead cell remains dead.

### Symmetric Encryption Scheme
A symmetric encryption scheme is defined using an encryption key derived from an initial configuration **S0** and its **k-evolution**. The key is represented as **< S0, k >**, which is a one-dimensional array of bits obtained by concatenating the rows of the extended matrix **Sk**.

For example, starting with **S0** and applying a **1-evolution**, we obtain an extended matrix **S1**, leading to the computed encryption key **< S0, 1 >**, represented as:
```
0 0 0 0 0 0 0 0 1 0 0 0 0 0 0 0 1 0 0 0 0 0 0 0 0 0 0 0 0 0
```
Given a plaintext message **m** (a string without spaces), encryption **{m}<S0,k>** is performed by XOR-ing **m** with **< S0, k >**, following these cases:
- If the message and key have the same length, they are XOR-ed element by element.
- If the message is shorter than the key, only the first part of the key is used.
- If the message is longer than the key, the key is repeated until it matches the message length.

## Requirements

### Task 0x00
- Read from **STDIN**: matrix dimensions (m, n), number of live cells (p), positions of live cells, and an integer **k**.
- Compute and display the state of the system after **k** evolutions.

### Task 0x01
- Read from **STDIN**: matrix dimensions (m, n), number of live cells (p), positions of live cells, an integer **k**, an integer **o** (0 for encryption, 1 for decryption), and a message **m** (plaintext for encryption, a **0x...** string for decryption).
- Perform encryption/decryption based on the calculated key **< S0, k >** and output the result.

### Task 0x02
- Rewrite **Task 0x00** in a separate source file, reading input from **in.txt** and writing output to **out.txt**, using C language functions for file handling.
