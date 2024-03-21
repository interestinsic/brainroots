
This is a **summary** of what you need to know for the **final CO Exam**, be aware that this is **a distilled version** of what has been seen in the tutorials
- You can find good (and probably better) resources on lausta's [CS Hub](https://lausta.notion.site/CS-Hub-6e7cae889f844cb59ae5f1809c88e553)

# Cheat Sheet
> Preferrably Memorized

- [[Basic Processing Unit (CISC, single bus).png]]
- Amdal's Law: $S_N=\frac{N}{N*s+p}$
- Gustafson's Law: $S_N=s+N*p$
- [[#Locality Principles]]



****
# Basic Processing Unit
## Components
![](Basic%20Processing%20Unit%20(CISC,%20single%20bus).png)
**PC**: Program Counter
**IR**: Instruction Register
**MAR**: Memory Adress Register
**MDR**: Memory Data Register

## Control Sequences
### Fetch Request Cycle
1. PC$_{out}$, MAR$_{in}$, READ, CONST=4, MUX$_{select}$=CONST, ALU$_F$ = ADD, Z$_{in}$ : 
	- Request Read from memory and increase counter by 4
2. Z$_{out}$, PC$_{in}$, WMFC : 
	- Save next execution adress in PC and wait for memory to arrive
3. MDR$_{out}$, IR$_{in}$ 
	- Save the instruction fetched from memory into IR

> Each line (1, 2, 3...) is what happens in one **Clock Cycle**, eg. a maximum of 1 CPU Bus write-read
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

- **Synchronous Bus**: There is a common clock signal for which data transfer read/write data at the same rate.
- **Asynchronous Bus**: The handshake protocol is used instead so both endpoints acknowledge to each other when they sent/received data.

# Pipelining & Parallelization
Stages
1. Fetch
2. Decode 
3. Execute
4. Write

Metrics
- **Latency**: the time it takes for one single instruction to complete ($x$ $cycles$)
- **Throughput**: the number of instructions we are completing in a given time unit ($x$ $instructions/cycle$)
## Pipelining

### Basic
We use stages to increase the **Throughput** by overlaping certain parts of instructions over each other.

**Pipeline Stalls**: Can be caused by:
- Memory access
- Branching
- Data dependency
- Long Operation


### Superscalar
Simmilar to Basic Pipelining, only that we have more than unit
- eg. 2 **Decode units**

**in-order commits**: mean that the instructions finish in the order they started, even if that means waiting of some instructions so that the order can be followed.

> [!TIP] Remember to:
> 1. Draw the complete pipeline tables
> 2. Check how many **instances** of eacth type of unit there are
> 3. Are the commits **in-order** or **out-of-order**?

## Parallelization
A program always has a **sequential** ($s$) and a **paralelizable** ($p$) part:
$$s + p = 1$$

### Amdal's Law
> With more processors... we can perform **the same** task in **less time**

The **time** for $N$ processors can be calculated as:
$$t_N=s+\frac{p}{N}$$


The **speedup** with this law can be calculated as:
$$S_N=\frac{t_1}{t_N}=\frac{s+p}{s+\frac{p}{N}}=\frac{1}{\frac{N*s+p}{N}}=\frac{N}{N*s+p}$$

The **bottleneck** is the **sequential fraction** ($s$)
- Because as $N$ increases the value $s$ will be bigger relative to the rest of the time equation
### Gustafson's Law
> With more processors... we can perform **a more difficult** task in **the same time**

The **speedup** can be calculated as:
$$S_N=s+N*p$$
%%AA Pending%%

