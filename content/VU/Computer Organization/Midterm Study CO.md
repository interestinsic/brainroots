# Cheat Sheet
> Preferrably Memorized, for speed

- [[Powers of 2]]
- [[Base 16 Symbols]]
- [[Formulas of all Logic gates]]
- [[Make every logic gate with NAND]]
- [[Special cases of IEEE-754.png]]

****

> I feel like what will be in the exam is just about the exercises they did during the tutorials
# Theory
## First computers and their hardware
- **ASCC**: One of the first general-purpose computers. (Not that much faster than doing operations by hand, frequent component failures)
- **ENIAC**: First **all-electronic** with **fully automated operations**. (Orders of magnitude faster, 20 Hours -> 20 Seconds. Still unreliable and power hungry)

## Generations (Historical Base)
1. First electronic digital computers (using vacuum tubes) were already using **Assembly** language to then translate it into machine code.
2. **Transistor** invented. Wide adaption of magnetic storage tech and the first high level languages (eg. Fortran)
3. New technologies emerge such as **Microprogramming**[^1], parallelism[^2] and pipelining[^3] and it's possible to add many transistors on a single silicon chip
4. Tens of thousands of transistors fit on a single chip, Microprocessor technology, CAD tools evolve, and it's possible to have computer communicate through networks, resulting in the formation of **Grid Computing**.
## Laws
- **More's Law**: Number of transistors in chips doubles every 1.5 Years (18 months).
- **Rock's Law**: The cost of a chip fabrication plant doubles every 4 Years.
- **Koomey's Law**: Energy efficiency doubles every 1.5 Years (18 months).


# Practical stuff
> For the first part of the exam it's recommended to take about 30sec, **1 minute max** per question.

## Karnaugh Maps
Used to find the minimum term expression for a given truth table.
To find an expression we group elements together in **power's of 2**. 
- The bigger the groups the better
- Overlap over the borders is possible
- Overlap between groups is possible
- *don't cares* **d** are elements that can be any value of 0 or 1
	- They can also be different for each group

There are two possible ways to represent them.


![[Different Karnaugh Map representations.png]]

> The second way is probably **easier and faster for the exam**.


## Synthesis of logical circuits (universal gates)
There exist two universal gates, the **NOR** and the **NAND** gate. The latter is used in most applications because it turns out to be faster. Through algebraic manipulation we can translate any expression into one of these Universal gates. 
Here is a quick example:
$$
f=(x+z)\cdot (\overline y + \overline w)
$$
<br>Involution
$$f=\overline{ \overline{(x+z)}}\cdot (\overline y + \overline w)$$
<br> De Morgan 
$$f=\overline{ (\overline x \cdot \overline z)}\cdot (\overline y + \overline w)$$
<br>De Morgan
$$f=\overline{ (\overline x \cdot \overline z)}\cdot \overline{(y \cdot w)}$$
<br>Involution 
$$f=\overline{\overline{(\overline{ (\overline x \cdot \overline z)}\cdot \overline{(y \cdot w)})}}$$
<br>Idempotence
$$f=\overline{\overline{(\overline{ (\overline{x \cdot x}  \cdot \overline{z \cdot z})}\cdot \overline{(y \cdot w)})}}$$
<br>Idempotence
$$f=\overline{\overline{(\overline{ (\overline{x \cdot x}  \cdot \overline{z \cdot z})}\cdot \overline{(y \cdot w)})} \cdot \overline{(\overline{ (\overline{x \cdot x}  \cdot \overline{z \cdot z})}\cdot \overline{(y \cdot w)})}}$$


## Multiplexers
It's a device that can select one from many input signals, and forward that signal as output.
![[Multiplexer_Implementation.png|400]]

It's important to know how to [implement certain functions](https://www.geeksforgeeks.org/multiplexers-in-digital-logic/) using **multiplexers**.
## Integer Representation
![[Binary Integer Representation.png|550]]

- **Unsigned Integer**: No fancy stuff, but it makes sense $2^3 + 2^2 + 2^1 + 2^0$
- **Sign and Magnitude**: Uses the first bits for the sign $\pm ( 2^2 + 2^1 + 2^0)$
- **1's Complement**[^4]: Inverts all the bits (except the sign bit) for negative values
- **2's Complement**: Inverts all the bits (except the sign bit) and adds 1 for all the negative values
- **Excess-N**: Adds a constant value before it gets stored, usually for it to fall in a specific range

## Radix conversions
> Usually with radix: $2, 8, 10, 16$

### Radix of powers of 2
Use grouping as a technique, for example $2^3 = 8$, so to convert a number **binary to octa** we can make groups of 3 bits:

![[Radix Conversions Bases 2.png]]
%%[[Radix Powers of 2 Conversions.excalidraw]]%%

> Pretty trivial to know your [[Powers of 2]]

### Other Radixes
For example when converting to base 10, we can not apply the grouping technique. So then we will just have to use the property of the exponents and the power to get the number translated. 

![[Radix Conversions Base 10.png]]

%%[[Radix conversions base 10.excalidraw]]%%

## Floating Point Representation & Conversion
> IEEE-754 [Floating Point Converter](https://www.h-schmidt.net/FloatConverter/IEEE754.html) nice for practising
> If you still don't understand how it works, here is a good [WikiHow article](https://www.wikihow.com/Convert-a-Number-from-Decimal-to-IEEE-754-Floating-Point-Representation)


[^1]: An intermediary layer between the CPU hardware and the programmer-visible instruction set architecture. [Wikipedia](https://en.wikipedia.org/wiki/Microcode)
[^2]: Lot's of processes being executed simultaneously, (multitasking duhh). Wikipedia
[^3]: A set of data processing elements connected in series, where the output of one element is the input of the next one. Wikipedia
[^4]: The name "ones' complement" (sic) refers to the fact that such an inverted value, if added to the original, would always produce an "all ones" number. Wikipedia


****
%%
# IDK
- Pending state machine??
- SR latches, flipflops 🩴, t flipflop, etc
- Finding the most optimal NAND-gate-only circuit
- Implementation of truth tables into multiplexers
- 

%%
