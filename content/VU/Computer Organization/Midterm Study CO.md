# Cheat Sheet
> Preferrably Memorized, for speed

- [[Powers of 2]]
- [[Base 16 Symbols]]
- [[Formulas of all Logic gates]]
- [[Make every logic gate with NAND]]
- [[Special cases of IEEE-754.png]]

## Symbols for base 16

****

> I feel like what will be in the exam is just about the exercises they did during the tutorials.
# To Know / Understand

## Theoretical Base
### First computers and their hardware
0. Electro Mechanical Devices
	- ASCC: One of the first general-purpose computers. (Not that much faster than doing operations by hand, frequent component failures)
	- ENIAC: First **all-electronic** with **fully automated operations**. (Orders of magnitude faster, 20 Hours -> 20 Seconds. Still unreliable and power hungry)

### Historical Base
Generations:
1. First electronic digital computers (using vacuum tubes) where already using **Assembly** language to then translate it into machine code.
2. **Transistor** invented. Wide adaption of magnetic storage tech and the first high level languages (eg. Fortran)
3. New technologies emerge such as **Microprogramming**[^1], parallelism[^2] and pipelining[^3] and it's possible to add many transistors on a single silicon chip
4. Tens of thousands of transistors fit on a slingle chip, Microprocessor technology, CAD tools evolve and it's possible to have computer communicate through networks, resulting in the formation of **Grid Computing**.
### Laws
- **More's Law**: Number of transistors in chips doubles every 1.5 Years (18 months).
- **Rock's Law**: The cost of a chip fabrication plant doubles every four 4 Years.
- **Koomey's Law**: Energy efficiency doubles every 1.5 Years (18 months).


## Practical stuff

### Karnaugh Maps

### Synthesis of logical circuits (universal gates)

### Multiplexers
![[Multiplexer_Implementation.png|300]]

### Integer Representation
![[Binary Integer Representation.png|300]]

### Radix conversions
> Usually with radix: $2, 8, 10, 16$

### Floating Point Representation & Conversion


[^1]: An intermediary layer between the CPU hardware and the programmer-visible instruction set architecture. [wikipedia](https://www.wikipedia.org/Microprogramming)
[^2]: Lot's of processes being executed simultaneously, (multitasking duhh). Wikipedia
[^3]: A set of data processing elements connected in series, where the output of one element is the input of the next one. Wikipedia


****
%%
# IDK
- Pending state machine??
- SR latches, flipflops 🩴, t flipflop, etc
- Finding the most optimal NAND-gate-only circuit
- Implementation of truth tables into multiplexers
- 

%%
