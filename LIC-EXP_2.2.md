CMOS Amplifier with Active Load (M<sub>1</sub>, M<sub>3</sub> NMOS and M<sub>2</sub> PMOS)
Circuit Description

This circuit consists of two NMOS transistors (M<sub>1</sub>, M<sub>3</sub>) and one PMOS transistor (M<sub>2</sub>).  
M<sub>3</sub> acts as a biasing device, M<sub>1</sub> acts as the amplifying transistor, and M<sub>2</sub> serves as the active load.  
The design ensures all transistors operate in the saturation region, enabling proper analog amplification and maximum output swing.  


Design Parameters

Supply Voltage
V<sub>DD</sub> = 1.8V

Maximum Power
P ≤ 1mW

Maximum Drain Current

I<sub>D(max)</sub> = P / V<sub>DD</sub>

I<sub>D(max)</sub> = 555.5µA

Chosen Drain Current

I<sub>D</sub> = 400µA

---

Overdrive Voltage Design

For maximum symmetrical swing, the overdrive voltage is selected carefully.

Maximum Overdrive Voltage

V<sub>ov(max)</sub> = V<sub>DD</sub> / 3

V<sub>ov(max)</sub> = 1.8 / 3

V<sub>ov(max)</sub> = 0.6V

Minimum Overdrive Voltage

V<sub>ov</sub> = 0.6 / 2

V<sub>ov</sub> = 0.3V

---

Operating Conditions
Saturation Constraints

**For M<sub>3</sub>**

V<sub>DS3</sub> ≥ V<sub>ov</sub>

V<sub>X</sub> ≥ V<sub>ov</sub>

V<sub>X(min)</sub> = V<sub>ov</sub>

**For M<sub>1</sub>**

V<sub>DS1</sub> ≥ V<sub>ov</sub>

V<sub>out</sub> ≥ V<sub>X</sub> + V<sub>ov</sub>

**For M<sub>2</sub>**

V<sub>SD2</sub> ≥ V<sub>ov</sub>

V<sub>DD</sub> − V<sub>out</sub> ≥ V<sub>ov</sub>

Output Voltage Range

Minimum Output Voltage

V<sub>out(min)</sub> = 2V<sub>ov</sub>

V<sub>out(min)</sub> = 0.6V

Maximum Output Voltage

V<sub>out(max)</sub> = V<sub>DD</sub> − V<sub>ov</sub>

V<sub>out(max)</sub> = 1.5V

Therefore

2V<sub>ov</sub> ≤ V<sub>out</sub> ≤ V<sub>DD</sub> − V<sub>ov</sub>

---

Optimum Output Voltage

V<sub>out</sub> = (V<sub>DD</sub> + V<sub>ov</sub>) / 2

V<sub>out</sub> = (1.8 + 0.3) / 2

V<sub>out</sub> = 1.05V

---

Output Swing

V<sub>swing</sub> = V<sub>DD</sub> − 3V<sub>ov</sub>

V<sub>swing</sub> = 1.8 − 0.9

V<sub>swing</sub> = 0.9V

---

**Gate Voltage Calculations**
NMOS

Threshold Voltage

V<sub>tn</sub> = 0.366V

Minimum

V<sub>GS(min)</sub> = 0.366V

Maximum

V<sub>GS(max)</sub> = 0.366 + 0.6 = 0.966V

Chosen

V<sub>GS</sub> = 0.666V

---

PMOS

Threshold Voltage

|V<sub>tp</sub>| = 0.39V

Minimum

V<sub>SG(min)</sub> = 0.39V

Maximum

V<sub>SG(max)</sub> = 0.99V

Chosen

V<sub>SG</sub> = 0.69V

---

Bias Voltages

For M<sub>1</sub>

V<sub>in</sub> = V<sub>GS</sub> + V<sub>X</sub>

V<sub>in</sub> = 0.666 + 0.3

V<sub>in</sub> = 0.966V

For M<sub>3</sub>

V<sub>B2</sub> = 0.666V

For M<sub>2</sub>

V<sub>B1</sub> = V<sub>DD</sub> − V<sub>SG</sub>

V<sub>B1</sub> = 1.8 − 0.69

V<sub>B1</sub> = 1.11V

---


### DC Analysis

DC analysis ensures all transistors remain in saturation while maintaining the desired operating point.
The bias voltages are selected to satisfy all saturation constraints and achieve maximum symmetrical swing.

Simulation parameters

V<sub>DD</sub> = 1.8V
V<sub>B1</sub> = 1.11V
V<sub>B2</sub> = 0.666V
V<sub>in</sub> = 0.966V
V<sub>out</sub> ≈ 1.05V

![Image description](https://github.com/shreevathsa-ks/LIC-LAB/blob/main/EXP-2/DC_2.2.png?raw=true)

---


### Transient Analysis

Transient analysis was carried out to evaluate the time-domain response and gain of the amplifier.

Output Voltage

V<sub>out(max)</sub> = 1.080V
V<sub>out(min)</sub> = 1.021V

Output swing

V<sub>out</sub> = 59mV

Input Voltage

V<sub>in(max)</sub> = 975.56mV
V<sub>in(min)</sub> = 956.42mV

Input swing

V<sub>in</sub> = 19.14mV

Voltage Gain

A<sub>v</sub> = V<sub>out</sub> / V<sub>in</sub>

A<sub>v</sub> = 59 / 19.14

A<sub>v</sub> ≈ 3.08 ≈ 3 V/V

Gain in dB

A<sub>v(dB)</sub> = 20 log(A<sub>v</sub>)

A<sub>v(dB)</sub> = 9.77 dB

![Image description](https://github.com/shreevathsa-ks/LIC-LAB/blob/main/EXP-2/Transient_2.2.png?raw=true)

---

### AC Analysis

AC analysis is used to determine the frequency response and bandwidth of the amplifier.

Midband Gain

A<sub>v</sub> ≈ 3.07

A<sub>v(dB)</sub> ≈ 9.753 dB

3 dB Bandwidth

BW = 54.978 MHz


Unity Gain Bandwidth

UGB = A<sub>v</sub> × BW

UGB = 3.08 × 54.978 MHz

UGB ≈ 162.4767 MHz

Verification

UGB ≈ Midband Gain × Bandwidth

UGB ≈ 169.33 MHz

(Small deviation due to simulation approximations)

![Image description](https://github.com/shreevathsa-ks/LIC-LAB/blob/main/EXP-2/AC_2.2.png?raw=true)



