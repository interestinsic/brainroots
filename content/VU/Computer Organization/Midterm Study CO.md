# Cheat Sheet
> Preferrably Memorized, for speed

- [[Powers of 2]]
- [[Base 16 Symbols]]
- [[Formulas of all Logic gates]]
- [[Make every logic gate with NAND]]
- [[Special cases of IEEE-754.png]]

## Symbols for base 16

****

> I feel like what will be in the exam is just about the exercises they did during the tutorials
# Theory
## First computers and their hardware
- **ASCC**: One of the first general-purpose computers. (Not that much faster than doing operations by hand, frequent component failures)
- **ENIAC**: First **all-electronic** with **fully automated operations**. (Orders of magnitude faster, 20 Hours -> 20 Seconds. Still unreliable and power hungry)

## Generations (Historical Base)
1. First electronic digital computers (using vacuum tubes) where already using **Assembly** language to then translate it into machine code.
2. **Transistor** invented. Wide adaption of magnetic storage tech and the first high level languages (eg. Fortran)
3. New technologies emerge such as **Microprogramming**[^1], parallelism[^2] and pipelining[^3] and it's possible to add many transistors on a single silicon chip
4. Tens of thousands of transistors fit on a slingle chip, Microprocessor technology, CAD tools evolve and it's possible to have computer communicate through networks, resulting in the formation of **Grid Computing**.
## Laws
- **More's Law**: Number of transistors in chips doubles every 1.5 Years (18 months).
- **Rock's Law**: The cost of a chip fabrication plant doubles every four 4 Years.
- **Koomey's Law**: Energy efficiency doubles every 1.5 Years (18 months).


# Practical stuff
> For the first part of the exam it's recommended to take about 30sec, **1 minute max** per question.

## Karnaugh Maps
Used to find the minimum term expression for a given truth table.
There are two possible ways to represent them.

(Karnaugh Map images)

> The second way is probably easier and faster for the exam.


## Synthesis of logical circuits (universal gates)
There exist two universal gates, the **NOR** and the **NAND** gate. The latter is used in most applications because it turns out to be faster. Through algebraic manipulation we can convert any expression by using one of these Universal gates. 
Here is a quick example:
(add an example)

## Multiplexers
![[Multiplexer_Implementation.png|300]]

## Integer Representation
![[Binary Integer Representation.png|300]]

## Radix conversions
> Usually with radix: $2, 8, 10, 16$

Also, with the procedure for grouping the stuffs together

## Floating Point Representation & Conversion

(Procedure for transforming base 10 to floating point and the other way around, with example)

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
