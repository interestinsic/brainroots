# Cheat Sheet

|     |      |
| --- | ---- |
$1KB = 10^3$ Bytes $\approx 1KiB = 2^{10}$ bytes
$1MB = 10^6$ Bytes $\approx 1MiB = 2^{20}$ bytes
$1GB = 10^9$ Bytes $\approx 1GiB = 2^{30}$ bytes
$1TB = 10^{12}$ Bytes $\approx 1TiB = 2^{40}$ bytes

We are using the [OSI model](https://en.wikipedia.org/wiki/OSI_model?oldformat=true)
- Each layer appends information, similar to a stack structure


![](UDP%20Encapulation.png)
****
# Physical Layer

## Topology
**Hierarchical topology**: Used by traditional phone networks, 
- Uses switching offices, centralized nodes through which most of the data has to travel
- More vulnerable when some central nodes fail.

**Mesh structure**: Used by the ARPANET
- Multiple nodes are connected to each other in a decentralized manner
- Different routes to the same destination
- Data structured in packets (that store message, but also sender and destination addresses)
- More Fault tolerant

**Modulation**: Convert bits into an analog signal // **Demodulation**: Convert analog signal into bits

## Channel Properties
- **Bit Rate**: $bits/sec$ (data transferred per unit time)
- **Delay**: $sec$ (time for data to arrive at the other end)
- **Storage Capacity**: $bits =(bits/sec)\times sec$ (how much data can be in the channel while being transferred)
	- $=$ Bitrate $\times$ Delay 
- **Error Rate:** Probability of bits flipping
	- Caused by Noise, Attenuation…

## Channel Types

### Wired
**Twisted pair**: twisted to cancel out noise that gets created
- Used in: Telephone networks and Wired LANs
- Bandwidth: up to 500MHz
- Example: CAT 6 cables

**Coaxial cable:** One single coper fiber, insulated in multiple layers
- Used in: Telephone networks, Cable television and in MANs[^1]
- Bandwidth: multiple GHz

**Optical fiber:** Thin glass sheet that can carry light thanks to critical angle reflection
- Used in: Long-distance networks, MANs[^1] and High-performance LANs[^2]
- Bandwidth: multiple 100 GHz

### Wireless
We communicate across the electromagnetic spectrum:

![](Radio%20Wave%20Spectrum.png)
([Wireless Communication spectrum](https://research-assets.cbinsights.com/2019/01/20155505/5G-Spectrum.png))


**Radio**: Can travel long distances and is cheap, but limited quality and amount.
- AM radio: $1 MHz$
- FM radio: $100 MHz$

**Microwave**: Can travel long distances, higher bandwidth, but needs **line of sight**.
- Satellite Communication: $\approx 10 MHz$
	- The higher latency makes it challenging

## Information Theory
We convert our data into a **wave**:

$$
y(t)=A\cdot sin(2\pi f t + \phi)
$$
- Amplitude ($A$)
- Frequency ($f$)
- Phase ($\phi$)

(Frequency and Phase are dependent)


### Nyquist's theorem - Noiseless channel
> maximum data rate for Noiseless channel

$$
R=2B \times \log_2{(V)}
$$

- $R$: maximum **data rate** ($bits/sec$)
- $B$: bandwidth[^3] ($Hz$)
- $V$: number of [discrete signal levels](https://en.wikipedia.org/wiki/Digital_signal?oldformat=true#/media/File:5PAMlevels.png) ($Integer$)

>[!TIP]- Example
> *Signal with 4 signal levels over a wired channel with 500kHz bandwith* <br>
> ($B=500,000 Hz$  ;  $V=4$) <br>
> $R=2\times 500,000 \times log_2{(4)}$ <br>
>  $R=2\times 500,000 \times log_2{(2^2)}$ <br>
> $R=2,000,000$ <br>
> $R= 2\cdot 10^6$ <br>
> $R=2Mbps$ <br>

### Shannon's theorem - Noisy channel
> maximum data rate for a Noisy channel

$$
R = B \times \log_2{\left(1+\frac{S}{N}\right)}
$$
- $R$: maximum **data rate** ($bits/sec$)
- $B$: bandwidth[^3] ($Hz$)
- $\frac{S}{N}$: Signal to Noise **ratio** ($dB$[^4]), **expressed in decibel**

>[!TIP]- Example
>Consider 4 signal levels, 500kHz Bandwith <br>
>$R=B\times log_2{(1+\frac{S}{N})}$ <br>
>$B=500,000$ <br>
>$\frac{S}{N}=40dB=10^{\frac{40}{10}}=10^4=10,000 \approx 2^{13}$  ($2^{13}=2^{10}\cdot 2^3=8192$) <br>
> $R=500,000 \times \log_2{1+2^{13}}$<br>
> $R=500,000 \times 13 = 6,500,000bit/sec = 6.5 Mbps$

## Digital Modulation
> How we represent our bits in the analog wave

![](Signal%20Encoding%20Modulation.png)

**Non-Return to Zero**: Represents a positive voltage and negative voltage for 1 and 0 respectively
- has **clock recovery** problems (because there may be long lists of where the signal is constant)

**Manchester Encoding**: Needs double the bandwidth

**4B/5B Encoding**: Uses a Translation table to map 4 bits of data onto 5.

**Scrambling**: XORing the data with a random bit sequence

### Passband Transmission
> Transmitting signals in a certain band that doesn't start at 0.

(Baseband starts at 0Hz)

We transmit data at higher frequencies, ($[S, S+B] Hz$) because low frequency signals may not be useful for wireless communication due to:
- **Antenna size**
- **Interference**

#### Phase Shift Keying
> From the signal composition, we can change the Phase ($\phi$) into different categories to encode more data in the signal.

**Binary Phase Shift**:
- Adding 2 symbols ($\phi = 0$ and $\phi = 180$) ($0, 1$)

**[[Quadrate Phase Shift Keying.png|Quadrature Phase Shift]]**: 
- Adding 4 symbols ($\phi=45, 135, 225, 315$) ($00, 01, 11, 10$)



(And so on…)
%%Pending%%
> [!TIP]- Example
> Exercise

## Multiplexing
> Transfer **multiple signals through a single medium**

**Simplex Channels**: Data can only pass through in one direction $\rightarrow$
**Duplex Channels:** Data can pass through in both directions at the same time $\iff$
**Half-duplex Channels:** Data can pass through both directions, but only one at a time $\leftrightarrow$

### Frequency Division Multiplexing
Different frequencies are used to transmit data to avoid interference with other signals. 
- For wireless networks, this makes it possible for multiple stations to send at the same time

### Time Division Multiplexing
Data gets sent on a fixed schedule to allow different data streams on the same line.
- Used in telephone/cellular networks

### Code Division Multiplexing
> aka. Code Division Multiple Access (CDMA)

It does by assigning a certain "chips" that are unique identifiers for each device
- Device A's *chip sequence* could be: ($1,-1,-1,1$) = 1
- For device A to show a 0, it would use the inverse *chip sequence* ($-1,1,1,-1$) = 0
- All of these sequences get added together, and then the receiver device can decode them.

%%Pending%%

****
# Data Link Layer
> Groups bits into individual frames (packets) that can be transmitted.
%%> - Offers “sending frames over a link” as a service to the network layer
> - Handles transmission errors
> - Regulates data flow%%


## Framing
> We need a way to indicate the start and endings of a frame.

### Byte count
> At the start of each frame we indicate how long it is.

- **Advantages:** Doesn't use that much overhead.
- **Disadvantages:** If one bit flips, all the remaining frames will also be read incorrectly.

### Byte Stuffing
> Using a flag byte to indicate starts and endings of a frame

- **Advantages**: Still easy to implement
- **Disadvantages**: Ways needed to still represent that flag bit character if it appears in the message contents (escaping needed)
	- It can also be space inefficient.


![](Byte%20Stuffing,%20escaping.png)

### Bit Stuffing
> Similar to Byte Stuffing, but with less overhead

- Instead of a Flag Byte we use a **bit pattern**
- Instead of an Escape Byte we **Insert a single bit** (in the bit pattern)

**Sender Algorithm**
1. Read the frame data
2. Stuff the bit patterns that appear in the message data ($01111110 \rightarrow 01111100$)
3. Add the bit pattern between each frame (eg. $01111110$)

**Receiver Algorithm**
1. Identify bit pattern (eg. $01111110$) and split it into frames.
2. Remove the bits that were stuffed (eg. $0111111$ <s>0</s>)
3. Read the data from the frame

## Flow Control
> How do we transfer data, and ensure its correct arrival?

### Stop-and-Wait

**Stop-and-Wait Protocol**: We send a message, and only when we receive and acknowledgement we send the next one.
- If we don't receive an acknowledgement back, we resend the previous message.

**Automatic Repeat ReQuest (ARQ)**: *Guaranteed Delivery over Unreliable Channel*
- The addition of sequence numbers to the frames. (to identify correct acknowledgements)
- Wait until previous frame has been accepted.
- We can make it more efficient by sending messages and ACK at the same time *Piggybacking*

### Sliding windows %%Revise%%
> Stop-and-Wait reduces its data rate when latency gets bigger

Sends more frames at once, instead of waiting for the next acknowledgement.

## Error Detection

We correct errors by **adding redundant bits**, where the total information sent is referred as the **Codeword**:
$$
n=m+r
$$
$m$: message
$r$: redundant bits
$n$: Codeword

The **code rate** is the amount of useful information (message $m$) in relation to the total data (codeword $n$)

$$
\frac{m}{n}
$$

**Hamming Distance**

>*minimum number of substitutions required to change one string into the other*

(In this context) It's the amount of bit flips (distance) needed to convert one bit sequence into another.
- $100 \rightarrow$ **2 bit flips** $\rightarrow 111$

We can use this concepts by creating codewords that represent single 1 or 0 bits.
> [!TIP]- Example
> *How many single bit errors can we detect with the following codewords ($000111, 111111, 000000$)?* <br>
> They have a **Hamming Distance** of 3 (we need 3 bit flips to transform one into the other) <br>
> We can **detect** $3-1=2$ single bit errors (eg. $011111$: Error!) <br>


### Parity
- Usually adding a single bit to the end of the message.
- Only detects an **odd** number of errors (two errors of 1 bit flip would cancel each other out)
#### Even Parity
**Adding a single bit** such that **the sum of 1's is even**.
> [!TIP]- Example
>**Send:** $1110000\rightarrow 11100001$
>**Recieve:** $11010101$ (Error detected!)
#### Odd Parity
**Adding a single bit** such that **the sum of 1's is odd**.
> [!TIP]- Example
>**Send:** $1110000\rightarrow 11100000$
>**Recieve:** $11010111$ (Error detected!)

#### Multiple Parity bits
We can also divide the message into blocks of n bits, and add an parity bit to each one.
- Helpful for detecting [[Parity Bit, burst errors.png|burst errors]].
- Helpful to **correct** errors. 

### Checksums
Splits the data into N-bit words (blocks), adds them together (reusing the carry bit) and appends the sum to the data.
- Better error detection than parity bits
- Detect bursts up to N errors
- Vulnerable to systematic errors (e.g. added zeros)

> Internet checksum uses one's complement arithmetic

> [!TIP]- Example
> We want to transmit $10110101$
> Split into 2 words (of 4 bits)
> $1011 + 0101 = 0001$ (one's complement addition, overflow get's added back to the start)
> **Inverted:** $1110$
> **Message:** $10110101$ $1110$
> $1011 + 0101 + 1110 = 1111$ (No error!)

### Cyclic Redundancy Check
The message gets divided by a **Generator polynomial** and the remainder gets appended
- The receiver will divide the total received codeword by the same generator polynomial, and get 0 as a remainder

## Error Correction
For an error with **Hamming distance** $n$. We can **correct** that contain up to the following changes:
$$
\left\lfloor \frac{n-1}{2} \right\rfloor
$$
### Hamming Codes
> A good [video](https://youtu.be/X8jsijhllIA?si=CBtpvs4NFx0Dx0Qi&t=578) from 3B1B

From a message we create a bigger codeword, in which **we reserve the power's of 2's indexes**, to store the redundant bits.
- For each power of 2 bit, we sum the 1's that appear all other numbers that contain that power.

<br>
![](Hamming%20Codes%20Visualization.png)

Here is an example of a hamming code computation for the message: $10011010$

| Index     | $1$ | $2$ | 3   | $4$ | 5   | 6   | 7   | $8$ | 9   | 10  | 11  | 12  |
| --------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Structure | _   | _   | 1   | _   | 0   | 0   | 1   | _   | 1   | 0   | 1   | 0   |
| Encoded   | 0   | 1   | 1   | 0   | 0   | 0   | 1   | 0   | 1   | 0   | 1   | 0   |

![](Hamming%20Code%20Table%20Wikipedia.png)
([Wikipedia, Hamming codes algorithm](https://en.wikipedia.org/w/index.php?title=Hamming_code&oldformat=true#General_algorithm))

When an error occurs in hamming codes, the order of the $p1, p2, p4, p8$ indicate the binary index of where the error bit is

### Convolutional Codes
%%Pending%%

## Medium Access Control
> Still part of layer 2 in the OSI model

### Ways to send data
- **Contend**
	- Always send data
	- Collisions will happen
	- Keep trying until sending succeeds
- Coordinate
	- Let other stations know before sending
	- Send when it's your turn
	- Wait, while others are sending

### Pure ALOHA[^5]
The users will always transmit frames when they can (like **Content**)
- If a collision occurs, users retry after a random delay.
- Send until we get an acknowledgement back.

> Problem: CSMA even if the frames **overlap a little bit**.

### Slotted ALOHA
Have a clock signal, by which all users agree that they will send in predefined time *slots*.
- This way frames are less likely to collide

### Carrier **Sense** Multiple Access (CSMA)
The users are able to check if the channel is occupied (*sense*) before sending data.
#### 1-Persistent CSMA
Only send when the channel is free. (But check constantly if it's free)

![](Midterm%20study%20CN%202024-04-20%2022.11.04.excalidraw)

#### non-Persistent CSMA
Only send when the channel is free. (When it's occupied wait a little)
![](Midterm%20study%20CN%202024-04-20%2022.15.44.excalidraw)

#### p-Persistent CSMA
> For **Slotted Channels**

Wait until channel is free, then send with a probability $p$
![](Midterm%20study%20CN%202024-04-20%2022.19.37.excalidraw)


### CSMA/CD
> CSMA with **Collision Detection**, if we detect a collision we stop sending the rest of our data.
> The basic protocol behind LAN

### Ethernet

#### 802.3 Ethernet
> We use 1-persistent CSMA/CD

%%Pending%%

**Collision Detection**
- Collisions can occur and take as long as $2t$ ($t$ being the time it takes to propagate over Ethernet)
- So the minimum packet size for detection is $s_f=2t \times R$
	- So that any transmission is **long enough** for a collision to be detected **before the transmission ends**.

**Ethernet frames:**

| Frame       |     | Preamble                            | Destination<br>Address | Source<br>address | T/L                                               | Data   | P                                                   | CRC                                                        |
| ----------- | --- | ----------------------------------- | ---------------------- | ----------------- | ------------------------------------------------- | ------ | --------------------------------------------------- | ---------------------------------------------------------- |
| bits        |     | 8                                   | 6                      | 6                 | 2                                                 | 0-1500 | 0-46                                                | 4                                                          |
| Description |     | Indicate the start <br>of the frame | MAC address            | MAC address       | Type (which network <br>layer protocol) or Length |        | Used if frame is less than <br>minimum frame length | 32-bit Cyclic Redundancy <br>Check for error **detection** |

#### Ethernet Switching
We have incoming LAN cables and over the time populate a look-up table with the corresponding destination ports for what destination each cable is giving us
- At the beginning we will get a lot of addresses wrong, but after some sync time it will all work.


![](Ethernet%20Switch.png)


**Spanning Trees**:
%%Pending%%

### 802.11 WiFI
> Unlike wired networks: We can't detect collisions, and we get *hidden* and *exposed* terminals.

#### CSMA/CA (Collision Avoidance)
**Physical channel sensing**: Check if the channel is in use.
**Virtual channel sensing**: Wait for acknowledgements before being able to send.
%%Pending%%

%%Pending last part Lecture 5, page 67%%



[^1]: Wired Metropolitan Area Networks
[^2]: Local Area Networks
[^3]: The width, usually measured in Hz, of a [frequency band](https://en.wikipedia.org/wiki/Radio_spectrum?oldformat=true#Waveguide_frequency_bands). 
[^4]: To convert from dB to normal units: $x \rightarrow 10^{x/10}$ (e.g.: $20$db = $10^2$, $40$db = $10^4$, $80$db = $10^8$)
[^5]: The system used by the University of Hawaii for one of the first high frequency wireless communication channels.
