# LIC-LAB EXPERIMENT-1
## Introduction.

A Common Source (CS) amplifier is a basic MOSFET amplifier configuration widely used for voltage amplification in analog circuits. In this configuration, the source terminal is common to both input and output, the input is applied at the gate, and the output is taken from the drain. A small change in gate-to-source voltage produces a change in drain current, which creates an amplified voltage across the drain resistor. The output signal is inverted, resulting in a 180° phase shift with respect to the input.

The voltage gain of a CS amplifier mainly depends on the transconductance of the MOSFET and the drain resistance. Its frequency response consists of three regions: low frequency, mid-band, and high frequency. In the mid-band region, the gain remains approximately constant. At low frequencies, coupling and bypass capacitors reduce the gain, while at high frequencies, internal capacitances of the MOSFET cause the gain to fall. The bandwidth is defined by the lower and upper cutoff frequencies where the gain drops by 3 dB from its mid-band value.

(picture of a cs amplifier and graph of 180 phase shift,and frequency responce(if possible all in one))

# EXPERIMENT-1:
## AIM

To design a CS-Amplifier using Nmosfet in tsmc 180nm tech.lib in LTspice with V<sub>DD</sub> as 1.8V, P<=1mW, C<sub>L</sub> = 10pF and L<sub>n</sub> = 560nm
--
**Using the tsmc tech.lib file we can get the other parameters like**
* Threshold Voltage (V<sub>th</sub>) = 0.366V.  
* Tox = 4.1x10<sup>-9</sup>(Used to calculate C<sub>ox</sub>).  
* Electron mobility (μ<sub>n</sub>) = 273.809x10<sup>-4</sup>.  
* Relative Permittivity, ε<sub>r</sub> = 4
----

# DC Analysis:

##  Design of Common Source (CS) Amplifier

This experiment focuses on designing a Common Source (CS) amplifier using an **NMOS transistor** from the TSMC 180 nm technology library in LTspice. The design is carried out to satisfy the given power constraint while ensuring proper DC biasing for amplification.

---

##  Given Specifications

* Supply Voltage, V<sub>DD</sub> = 1.8 V
* Maximum Power Dissipation, P ≤ 1 mW
* Load Capacitance, C<sub>L</sub> = 10 pF
* Channel Length, L<sub>n</sub> = 560 nm
---

##  Power Constraint and Drain Current Selection

From the power constraint:  
P = V<sub>DD</sub> × I<sub>D</sub>  
I<sub>D</sub> ≤ 1 mW / 1.8 V  
I<sub>D</sub> ≤ 0.555 mA  
To stay safely within limits, we choose:  

I<sub>D</sub> = 400 µA  
---

##  Drain Resistor Calculation

For maximum symmetrical swing, the drain voltage is biased at mid-supply:  
V<sub>D</sub> ≈ V<sub>DD</sub> / 2 = 0.9 V  
R<sub>D</sub> = (V<sub>DD</sub> − V<sub>D</sub>) / I<sub>D</sub>  
R<sub>D</sub> = (1.8 − 0.9) / 400 µA  
R<sub>D</sub> = 0.9 / 400 × 10<sup>-6</sup>  

R<sub>D</sub> = 2250 Ω
---

##  Oxide Capacitance Calculation

Oxide capacitance per unit area:  
C<sub>ox</sub> = ε<sub>ox</sub> / T<sub>ox</sub>  
Where:  
ε<sub>ox</sub> = ε<sub>r</sub> × ε<sub>0</sub>  
ε<sub>0</sub> = 8.854 × 10<sup>-12</sup>  
ε<sub>ox</sub> = 4 × 8.854 × 10<sup>-12</sup>  
ε<sub>ox</sub> = 3.5416 × 10<sup>-11</sup>  
C<sub>ox</sub> = (3.5416 × 10<sup>-11</sup>) / (4.1 × 10<sup>-9</sup>)  

C<sub>ox</sub> ≈ 8.64 × 10<sup>-3</sup> F/m²
---

##  Bias Condition
Chosen gate voltage:  
V<sub>GS</sub> = 0.9 V  
Overdrive voltage:  
V<sub>OV</sub> = V<sub>GS</sub> − V<sub>th</sub>  
V<sub>OV</sub> = 0.9 − 0.366  

V<sub>OV</sub> = 0.534 V  
---

##  Drain Current Equation (Saturation Region)

For MOSFET operating in saturation:  
I<sub>D</sub> = (1/2) μ<sub>n</sub> C<sub>ox</sub> (W/L) (V<sub>OV</sub>)²  
Using:  
 
* I<sub>D</sub> = 400 µA  
* L = 560 nm  
* μ<sub>n</sub> and C<sub>ox</sub> as calculated  
* V<sub>OV</sub> = 0.534 V  

The required transistor width W can be determined from this expression.
##  Transistor Width Calculation  
Using the saturation current equation:  
I<sub>D</sub> = (1/2) μ<sub>n</sub> C<sub>ox</sub> (W/L) (V<sub>OV</sub>)²  
Given:  
I<sub>D</sub> = 400 µA  
μ<sub>n</sub> = 273.809 × 10<sup>-4</sup> m²/V·s  
C<sub>ox</sub> = 8.64 × 10<sup>-3</sup> F/m²  
L = 560 nm  
V<sub>OV</sub> = 0.534 V  


Rearranging for W:  
W = (2 I<sub>D</sub> L) / (μ<sub>n</sub> C<sub>ox</sub> (V<sub>OV</sub>)²)  
Substituting the values:  
W ≈ 6.7 × 10<sup>-6</sup> m  

W ≈ 6.755 µm  
--
(pcture of ckt)  

But if we verify the same circuit with the same parameters, the I<sub>D</sub> value and the V<sub>GS</sub> 
value will not match the ones that we got from theoretical analysis.
If we change the Windth value we can obtain the desired current and voltage.
We got W as 9.087µm

--

(picture of ckt with o/p) 
write something abt it and finish DC 

--

TRANSIENT ANALYSIS  

###Simulation

Input applied:
Sine wave with AC amplitude = 10 mV, frequency = 1 kHz, DC offset = 0.9 V

From LTspice simulation:
V<sub>in</sub>(p-p) = 19.237 mV
V<sub>out</sub>(p-p) = 63.997 mV

Voltage gain (simulation):
A<sub>v</sub> = V<sub>out</sub>(p-p) / V<sub>in</sub>(p-p) ≈ 3.36

Gain in dB:
20 log(A<sub>v</sub>) = 10.438 dB

###Theoretical Gain Calculation

Using small signal relation:

g<sub>m</sub> = 2I<sub>D</sub> / V<sub>OV</sub>

g<sub>m</sub> ≈ 0.001498 S

A<sub>v</sub> = g<sub>m</sub> R<sub>D</sub>

A<sub>v</sub> ≈ 0.001498 × 2250 ≈ 3.37

The theoretical gain (~3.37) closely matches the simulated gain (3.36), validating the design.




