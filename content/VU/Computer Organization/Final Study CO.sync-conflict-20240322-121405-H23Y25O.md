
What you need to know for the final CO Exam, be aware that this is a distilled version of what has been seen in the tutorials
- You can find more nice (and probably better) resources on lausta's the [CS Hub](https://lausta.notion.site/CS-Hub-6e7cae889f844cb59ae5f1809c88e553)

# Cheat Sheet
> Preferrably Memorized

- 



****
# Basic Processing Unit
## Components
![](Basic%20Processing%20Unit%20(CISC,%20single%20bus).png)
**PC**: Program Counter
**IR**: Instruction Register
**MAR**: Memory Adress Register
**MDR**: Memory Data Register

> Each line (1, 2, 3...) is what happens in one **Clock Cycle**, eg. a maximum of 1 CPU Bus write-read


## Control Sequences
### Fetch Request Cycle
1. PC$_{out}$, MAR$_{in}$, READ, CONST=4, MUX$_{select}$=CONST, ALU$_F$ = ADD, Z$_{in}$ : 
	- Request Read from memory and increase counter by 4
2. Z$_{out}$, PC$_{in}$, WMFC : 
	- Save next execution adress in PC and wait for memory to arrive
3. MDR$_{out}$, IR$_{in}$ 
	- Save the instruction fetched from memory into IR
## Indirect Memory Accesses
Keeping into account how many times we read/write to memory
- **Add R1, R2** : 1
	1. Fetch
- **Add (R1), R2**: 2
	1. Fetch
	2. Read adress stored in R1
- **Add R1, (R2)**
	1. Fetch
	2. Read adress stored in R2
	3. Write into adress stored at R2

> We usually execute the WFMC just step before MDR$_{out}$, or right after a WRITE instruction
## Performance Analysis

### Fetch and Execution Times
Every clock cycle is given to take an $x$ amount of time and every memory acces is usually (a much higher) value $y$, and what we must do is along the execution of the program decide whether a line is a *normal clock cycle* or if it accesses memory (usually when WFMC appears)

## ISA Design
### Optcodes
They are a certain amount of bits at the beginning of an instruction that specifies the operation to be performed
- eg.  **1011** 101011: 4-bit optcode

### Opcode operations
The the bigger the optcode the less space for the possible proceding operands
%%AA Pending%%

# Memory and I/O Subsystems

## Memory

### Locality Principles
- **Temporal Locality**: Recent Items get reused (things close to each other)
- **Spacial Locality**: Nearby Items get reused (repeating things)

> More localities mean it's more easy to use the cache as an intermediary instead of having to always access memory


### Caches
**LRU**: Least Recently Used replacement algorithm
- The oldest memory block get's replaced by new incomming memory

A **set associaltive cache** is devided in Sets and Blocks
<br>
![](Set%20associative%20cache.png)

In this case the set size is 4, so the items will be stored in order of **X%4** (modulo)
![](Filled%20set%20associative%20cache.png)

#### Main Memory accesses vs Cache Accesses
%%AA Pending%%

## I/O Subsystem

### Polling and interrupts
- **Polling**: Periodic Checks (constant refreshing and fetching of data)
- **Interrupts**: Dependant on I/O data recieved


### Synchronous vs Asynchronous

- **Synchronous Bus**: 
- **Asynchronous Bus**: 

# Pipelining
