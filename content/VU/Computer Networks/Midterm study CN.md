# Cheat Sheet

|     |      |
| --- | ---- |
$1KB = 10^3$ Bytes $\approx 1KiB = 2^{10}$ bytes
$1MB = 10^6$ Bytes $\approx 1MiB = 2^{20}$ bytes
$1GB = 10^9$ Bytes $\approx 1GiB = 2^{30}$ bytes
$1TB = 10^{12}$ Bytes $\approx 1TiB = 2^{40}$ bytes

We are using the [OSI model](https://en.wikipedia.org/wiki/OSI_model?oldformat=true)
- Each layer appends information, simmilar to a stack structure


![](UDP%20Encapulation.png)
****
# Physical Layer

## Topology
**Hierarchichal topology**: Used by traditional phone networks, 
- Uses switching offices, centralized nodes through which most of the data has to travel
- More voulnerable when some central nodes fail.

**Mesh structure**: Used by the ARPANET
- Multiple nodes are connected to each other in a decentralized manner
- Different routes to the same destination
- Data structured in packets (that store message, but also sender and destination addresses)
- More Fault tolerant

**Modulation**: Convert bits into an analog signal // **Demodulation**: Convert analog signal into bits

## Channel Properties
- **Bit Rate**: $bits/sec$ (data transeferd per unit time)
- **Delay**: $sec$ (time for data to arrive at the other end)
- **Storage Capacity**: $bits =(bits/sec)\times sec$ (how much data can be in the channel while being transfered)
	- $=$ BitRate $\times$ Delay 
- **Error Rate:** Probability of bits flipping
	- Caused by Noise, Attenuation..

## Channel Types

### Wired
**Twisted pair**: twisted to cancel out noise that get's created
- Used in: Telephone networks and Wired LANs
- Bandwith: up to 500MHz
- Example: CAT 6 cables

**Coaxial cable:** One single coper fiber, insdulated in multiple layers
- Used in: Telephone networks, Cable television and in MANs[^1]
- Bandwith: multiple GHz

**Optical fiber:** Thin glass sheet that can carry light thanks to critical angle reflection
- Used in: Long-distance networks, MANs[^1] and High-performance LANs[^2]
- Bandiwth: multiple 100 GHz

### Wireless
We communicate across the electromagnetic spectrum:

![](Radio%20Wave%20Spectrum.png)
([Wireless Communication spectrum](https://research-assets.cbinsights.com/2019/01/20155505/5G-Spectrum.png))


**Radio**: Can travel long distances and is cheap, but limited quality and amount.
- AM radio: $1 MHz$
- FM radio: $100 MHz$

**Microwave**: Can travel long distances, higher bandwith, but needs **line of sight**.
- Satelite Communication: $\approx 10 MHz$
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


### Nyquist's theorem -  Noiseless channel
> maximum data rate for for Noiseless channel

$$
R=2B \times \log_2{(V)}
$$

- $R$: maximum **data rate** ($bits/sec$)
- $B$: bandwith[^3] ($Hz$)
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
- $B$: bandwith[^3] ($Hz$)
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

**Manchester Encoding**: Needs doble the bandwith

**4B/5B Encoding**: Uses a Translation table to map 4 bits of data onto 5.

**Scrambling**: XORing the data with a random bit sequence

### Passband Transmission
> Transmitting signals in a certain band that doesn't start at 0.

(Baseband starts at 0Hz)

We transmit data at higher frequencies, ($[S, S+B] Hz$) because low frequency signals may not be useful for wireless communication due to:
- **Antenna size**
- **Interference**

#### Phase Shift Keying
> From the signal composition, we can on purpos change the Phase ($\phi$) into different chategories to encode more data in the signal.

**Binary Phase Shift**:
- Adding 2 symbols ($\phi = 0$ and $\phi = 180$) ($0, 1$)

**[[Quadrate Phase Shift Keying.png|Quadrature Phase Shift]]**: 
- Adding 4 symbols ($\phi=45, 135, 225, 315$) ($00, 01, 11, 10$)



(And so on..)
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
- For wireless networks this makes it possible for multiple stations to send at the same time

### Time Division Multiplexing
Data get's sent on a fixed schedule to allow different data streams on the same line.
- Used in telephone/cellular networks

### Code Division Multiplexing
> aka. Code Division Multiple Access (CDMA)

It does by assigning a certain "chips" that are unique identifiers for each device
- Device A's *chip sequence* could be: ($1,-1,-1,1$) = 1
- For device A to show a 0, it would use the inverse *chip sequence* ($-1,1,1,-1$) = 0
- All of these sequences get added together, and then the reciever device can decode them.

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
> Simmilar to Byte Stuffing, but with less overhead

- Instead of a Flag Byte we use a **bit pattern**
- Instead of an Excape Byte we **Insert a single bit** (in the bit pattern)

**Sender Algorithm**
1. Read the frame data
2. Stuff the bit patterns that appear in the message data ($01111110 \rightarrow 01111100$)
3. Add the bit pattern between each frame (eg. $01111110$)

**Reciever Algorithm**
1. Identify bit pattern (eg. $01111110$) and split it into frames.
2. Remove the bits that where stuffed (eg. $0111111$ <s>0</s>)
3. Read the data from the frame

## Flow Control




[^1]: Wired Metroplitan Area Networks
[^2]: Local Area Networks
[^3]: The width, usually measured in Hz, of a [frequency band](https://en.wikipedia.org/wiki/Radio_spectrum?oldformat=true#Waveguide_frequency_bands). 
[^4]: To convert from dB to normal units: $x \rightarrow 10^{x/10}$ (eg: $20$db = $10^2$, $40$db = $10^4$, $80$db = $10^8$)