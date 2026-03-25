# LIC-LAB EXPERIMENT - 2
## Aim
### To Design the Amplifier Configuration using tsmc 180nm tech.lib in LT Spice 
**Parameters**

Supply Voltage  V<sub>DD</sub> = 1.8V  

Power Constraint  
P ≤ 1mW  

Maximum drain current  
I<sub>D(max)</sub> = P / V<sub>DD</sub>  
I<sub>D(max)</sub> = 1mW / 1.8  
I<sub>D(max)</sub> = 555.5µA  

Chosen drain current (safe margin)  
I<sub>D</sub> = 400µA  

Channel Length  L = 560nm  

Chosen Overdrive Voltage  
V<sub>ov</sub> = 0.25V 

---

**Calculations**
Source Resistor Calculation

Voltage across source resistor

V<sub>RS</sub> = 0.2V  
R<sub>S</sub> = V<sub>RS</sub> / I<sub>D</sub>  
R<sub>S</sub> = 0.2 / 400µA  
R<sub>S</sub> = 500Ω  

**Output Bias Voltage**

V<sub>out</sub> = V<sub>DD</sub>/2 + V<sub>RS</sub>  
V<sub>out</sub> = 1.8/2 + 0.2  
V<sub>out</sub> = 1.1V  

---


**NMOS Calculations**

Threshold Voltage   V<sub>thn</sub> = 0.366V   
Overdrive Voltage   V<sub>ov</sub> = 0.25V   

Gate Source Voltage  

V<sub>GS1</sub> = V<sub>thn</sub> + V<sub>ov</sub>  
V<sub>GS1</sub> = 0.366 + 0.25  
V<sub>GS1</sub> = 0.616V   

**Bias Voltage**  

V<sub>B1</sub> = V<sub>GS1</sub> + V<sub>RS</sub>   
V<sub>B1</sub> = 0.616 + 0.2  
<sub>B1</sub> = 0.816V   

---


**NMOS Width Calculation**

Drain Current Equation

I<sub>D</sub> = (1/2) µ<sub>n</sub> C<sub>ox</sub> (W/L) V<sub>ov</sub><sup>2</sup>
Given  
µ<sub>n</sub> = 273.81 × 10⁻⁴  
C<sub>ox</sub> = 8.6 × 10⁻³  
L = 560nm  

Solving for W  

W = 30.441µm  
Adjusted width used in simulation  
W<sub>n</sub> = 54µm  

---

**PMOS Calculations**

Threshold Voltage

V<sub>thp</sub> = −0.390V

Overdrive voltage relation

V<sub>ov</sub> = V<sub>SG</sub> − |V<sub>thp</sub>|

Given

V<sub>ov</sub> = 0.25V

Therefore

V<sub>SG</sub> = 0.64V

Source Voltage

V<sub>S</sub> = V<sub>DD</sub> = 1.8V

Gate Voltage

V<sub>G</sub> = V<sub>out</sub> = 1.1V

---

Bias Voltage

V<sub>B2</sub> = 1.16V

PMOS Width Calculation

Drain current equation

I<sub>D</sub> = (1/2) µ<sub>p</sub> C<sub>ox</sub> (W/L) V<sub>ov</sub><sup>2</sup>

Given

µ<sub>p</sub> = 115.68

µ<sub>p</sub>C<sub>ox</sub> = 9.7361 × 10⁻⁵

Solving for W

W = 73.56µm

Adjusted simulation width

W<sub>p</sub> = 165.255µm

---

### Transient Analysis

Transient analysis was performed to observe the small signal amplification capability of the circuit.

Measured Output Voltage

V<sub>out</sub> = (1375 − 840.591) mV

V<sub>out</sub> = 531.403mV

Measured Input Voltage

V<sub>in</sub> = (825.962 − 806.194) mV

V<sub>in</sub> = 19.768mV

**Voltage Gain**

A<sub>v</sub> = V<sub>out</sub> / V<sub>in</sub>

A<sub>v</sub> = 26.88

Gain in dB

A<sub>v(dB)</sub> = 20 log(A<sub>v</sub>)

A<sub>v(dB)</sub> = 28.58 dB

---

### AC Analysis

Without Load Capacitor

Midband Gain

28.76 dB

3dB Gain

25.76 dB

3dB Bandwidth

52.76 MHz

Unity Gain Bandwidth

UGB = A<sub>v</sub> × BW

UGB = 26.88 × 52.529 MHz

UGB ≈ 1.714 GHz

---

With Load Capacitor

**Midband Gain**

28.76 dB

3dB Gain

25.76 dB

3dB Bandwidth

772.338 kHz

**Unity Gain Bandwidth**

UGB = A<sub>v</sub> × BW

UGB = 26.88 × 772.338 kHz

UGB ≈ 21.216 MHz
