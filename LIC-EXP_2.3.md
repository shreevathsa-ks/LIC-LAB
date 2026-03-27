# Common Source Amplifier with Active Load and Diode-Connected NMOS  
**Circuit Description**  

The circuit consists of a PMOS transistor (M<sub>2</sub>) acting as an active load, a common-source NMOS transistor (M<sub>1</sub>), and a diode-connected NMOS transistor (M<sub>3</sub>) used for biasing.  
The diode-connected configuration ensures stable biasing current while maintaining all transistors in the saturation region.   

---

**Design Parameters**

Supply Voltage  
V<sub>DD</sub> = 1.8V  

Maximum Power  
P ≤ 1mW  

Maximum Drain Current

I<sub>D(max)</sub> = 555.5µA

Chosen Drain Current

I<sub>D</sub> = 400µA

Channel Length

L = 560nm

---

**Overdrive Voltage Design**

For maximum output swing

V<sub>swing</sub> = V<sub>DD</sub> − 3V<sub>ov</sub>

Condition for proper operation

V<sub>DD</sub> − 3V<sub>ov</sub> ≥ 0

Maximum overdrive

V<sub>ov(max)</sub> = V<sub>DD</sub> / 3 = 0.6V

Chosen overdrive voltage

V<sub>ov</sub> = 0.3V

---

Saturation Conditions

For **M<sub>3</sub>**

V<sub>DS3</sub> ≥ V<sub>ov</sub>

V<sub>X(min)</sub> = V<sub>ov</sub> = 0.3V

For **M<sub>1</sub>**

V<sub>DS1</sub> ≥ V<sub>ov</sub>

V<sub>out</sub> ≥ V<sub>X</sub> + V<sub>ov</sub>

For **M<sub>2</sub>**

V<sub>SD2</sub> ≥ V<sub>ov</sub>

V<sub>DD</sub> − V<sub>out</sub> ≥ V<sub>ov</sub>

---

**Output Voltage Range**

V<sub>out(min)</sub> = 2V<sub>ov</sub> = 0.6V

V<sub>out(max)</sub> = V<sub>DD</sub> − V<sub>ov</sub> = 1.5V

**Optimum Output Voltage**

V<sub>out</sub> = (V<sub>DD</sub> + V<sub>ov</sub>) / 2

V<sub>out</sub> = (1.8 + 0.3)/2

V<sub>out</sub> = 1.05V

---

Gate Bias Calculations  

NMOS

V<sub>tn</sub> = 0.366V

V<sub>GS</sub> = V<sub>tn</sub> + V<sub>ov</sub>

V<sub>GS</sub> = 0.366 + 0.3

V<sub>GS</sub> = 0.666V

PMOS

|V<sub>tp</sub>| = 0.39V

V<sub>SG</sub> = |V<sub>tp</sub>| + V<sub>ov</sub>

V<sub>SG</sub> = 0.39 + 0.3

V<sub>SG</sub> = 0.69V

---

**Bias Voltages**

V<sub>B2</sub> (M<sub>3</sub>) = 0.666V

V<sub>B1</sub> (M<sub>2</sub>) = 1.11V

Input Bias

V<sub>in</sub> = V<sub>GS</sub> + V<sub>X</sub>

V<sub>in</sub> = 0.666 + 0.3

V<sub>in</sub> = 0.966V

Transistor Dimensions

NMOS Width

W<sub>n</sub> = 430.2µm

PMOS Width

W<sub>p</sub> = 108.59µm

---

### DC Analysis

DC analysis confirms that all transistors operate in the saturation region and the desired operating point is achieved.  
The chosen bias voltages ensure proper current flow and symmetric output swing.  

**Operating point**

V<sub>out</sub> ≈ 1.05V

![Image description](https://github.com/shreevathsa-ks/LIC-LAB/blob/main/EXP-2/DC_2.3.png?raw=true)

---

### Transient Analysis

Transient analysis was performed to determine the voltage gain of the amplifier.

Output Voltage

V<sub>out(max)</sub> = 1.522V  
V<sub>out(min)</sub> = 0.5927V  

Output swing

V<sub>out</sub> = 929.59mV

Input Voltage

V<sub>in(max)</sub> = 975.99mV  
V<sub>in(min)</sub> = 956.02mV  

Input swing

V<sub>in</sub> = 19.97mV

Voltage Gain

A<sub>v</sub> = 929.59 / 19.97

A<sub>v</sub> = 46.54 V/V

Gain in dB

A<sub>v(dB)</sub> = 20 log(A<sub>v</sub>)

A<sub>v(dB)</sub> = 33.56 dB

![Image description](https://github.com/shreevathsa-ks/LIC-LAB/blob/main/EXP-2/Transient_2.3.png?raw=true)

---

### AC Analysis

AC analysis evaluates the frequency response of the amplifier.

Load Capacitor

C<sub>L</sub> = 10pF

**Midband Gain**

A<sub>v</sub> = 60.88 V/V

A<sub>v(dB)</sub> = 35.69 dB

3 dB Bandwidth

BW = 1.00 MHz

Verification

UGB ≈ Midband Gain × Bandwidth

UGB ≈ 60.88 × 1 MHz

UGB ≈ 60.88 MHz

(Closely matches simulated value, validating the design)

![Image description](https://github.com/shreevathsa-ks/LIC-LAB/blob/main/EXP-2/AC_2.3.png?raw=true)
