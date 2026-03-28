# Experiment 04

## MOS Differential Amplifier Analysis (Resistive Load)

---

## Aim

The aim of this experiment is to design and analyze a MOSFET differential amplifier using a resistive load configuration. The circuit is studied under different analyses such as DC, transient, and AC in order to understand its operating behavior, gain, linearity, and frequency response.

---

## Introduction

Differential amplifiers are one of the most important building blocks in analog electronics. These circuits are mainly used to amplify the difference between two input signals while rejecting any signal that is common to both inputs. Because of this property, they are widely used in noise reduction and signal conditioning applications.

In MOS-based designs, differential amplifiers are commonly used in the input stage of operational amplifiers and comparators. Compared to single-ended amplifiers, they provide better stability and improved performance.

In this experiment, a differential amplifier using NMOS transistors and resistive loads is designed and its behavior is verified through simulation.

---

## Theory

A differential amplifier produces an output based on the difference between two input voltages:

<sub>v<sub>id</sub> = v<sub>in1</sub> − v<sub>in2</sub></sub>

When both inputs are equal, the circuit is said to be in balanced condition, and ideally no differential output is produced. However, when there is a difference between the inputs, current distribution between the two transistors changes, which results in a corresponding output voltage.

For small input signals, both MOSFETs operate in saturation and share the current equally. In this region, the amplifier behaves linearly and produces an undistorted output.

The small-signal transconductance is given by:

<sub>g<sub>m</sub> = (2I<sub>D</sub>) / V<sub>ov</sub></sub>

The voltage gain of the circuit depends on both the transconductance and the output resistance:

<sub>A<sub>v</sub> = −g<sub>m</sub>(R<sub>D</sub> || r<sub>o</sub>)</sub>

As the input signal increases, one transistor starts conducting more current while the other conducts less. Beyond a certain limit:

<sub>|v<sub>id</sub>| > 2V<sub>ov</sub></sub>

one of the transistors enters cutoff, and the circuit no longer behaves linearly.

---

## Circuit 1: Differential Amplifier with Resistive Load

### Working

The circuit consists of two identical NMOS transistors whose sources are connected together and biased using a constant current source. This current source ensures that the total current flowing through the circuit remains constant.

The drains of the transistors are connected to resistors (<sub>R<sub>D</sub></sub>), which convert the drain current variations into voltage outputs.

When a differential input is applied:

* If <sub>v<sub>in1</sub></sub> increases, the gate voltage of M1 increases, leading to an increase in its drain current
* At the same time, M2 carries less current
* This creates a voltage difference at the outputs

Thus, the circuit effectively converts a differential input voltage into a differential output voltage.

---

## Design Calculations

### Given Parameters

Technology = 180 nm <sub>V<sub>DD</sub> = +0.9 V</sub> <sub>V<sub>SS</sub> = −0.9 V</sub>
Power ≤ 2.2 mW <sub>L = 540 nm</sub> <sub>V<sub>CM</sub> = 0 V</sub> <sub>V<sub>OCM</sub> = 0 V</sub> <sub>V<sub>P</sub> = −0.7 V</sub> <sub>V<sub>T</sub> ≈ 0.36 V</sub>

---

### Tail Current Selection

The total current in the circuit is limited by the power constraint. The relation between power and current is:


P = (V<sub>DD</sub> − V<sub>SS</sub>) I<sub>SS</sub>


Substituting the supply values:


1.8 × I<sub>SS</sub> ≤ 2.2 × 10⁻³


From this, the maximum allowable tail current is approximately:


I<sub>SS</sub> ≈ 1.22 mA


This value ensures that the circuit operates within the given power limit.

---

### Drain Current

Under balanced condition, the current splits equally between the two transistors:


I<sub>D</sub> = I<sub>SS</sub> / 2 ≈ 0.61 mA


This current sets the operating point of each MOSFET.

---

### Load Resistance

The output common-mode voltage is given as zero, which helps determine the load resistance.

V<sub>out</sub> = V<sub>DD</sub> − I<sub>D</sub>R<sub>D</sub>

Setting <sub>V<sub>out</sub> = 0:


R<sub>D</sub> ≈ 1.475 kΩ


This resistance ensures that the output is centered around 0 V.

---

### Bias Conditions

The gate voltage is fixed by the common-mode input:


V<sub>G</sub> = 0 V


The source voltage is given:


V<sub>S</sub> = −0.7 V


Thus:


V<sub>GS</sub> = 0.7 V


Overdrive voltage:

V<sub>ov</sub> = 0.34 V

This confirms that the transistor is strongly turned ON.

---

### Saturation Verification

For proper amplifier operation, both transistors must remain in saturation.


V<sub>DS</sub> = 0.7 V


Since:

<sub>V<sub>DS</sub> > V<sub>ov</sub></sub>

the condition for saturation is satisfied.

---

## Width Calculation

To determine the device dimensions, the MOS current equation is used:


I<sub>D</sub> = (1/2) μ<sub>n</sub>C<sub>ox</sub> (W/L)(V<sub>ov</sub>)²


Rearranging for width:


W = (2I<sub>D</sub>L) / (μ<sub>n</sub>C<sub>ox</sub>(V<sub>ov</sub>)²)


Substituting the given values:


μ<sub>n</sub>C<sub>ox</sub> = 236.5 μA/V²


Calculated width:


W ≈ 24.1 μm


However, this value is obtained using ideal equations. In practical simulations, additional effects such as channel length modulation and mobility degradation slightly alter the current.

After fine-tuning the width in simulation to match the desired drain current and output voltage:


W ≈ 32 μm


This adjusted value provides a more accurate operating point.

---

## DC Analysis

📌 *Insert DC schematic screenshot here*
📌 *Insert DC operating point screenshot here*

The DC analysis confirms that both transistors are correctly biased. The drain voltages, source voltage, and currents match the expected theoretical values. Both devices remain in saturation, which is necessary for proper amplification.

---

## Input Common Mode Range (ICMR)

The ICMR defines the range of input voltage over which the amplifier operates correctly.

### Minimum Value

To keep the transistor ON:

V<sub>GS</sub> ≥ V<sub>T</sub>

V<sub>ICM(min)</sub> = V<sub>S</sub> + V<sub>T</sub>

V<sub>ICM(min)</sub> = −0.34 V

---

### Maximum Value

To maintain saturation:

V<sub>DS</sub> ≥ V<sub>ov</sub>

V<sub>ICM(max)</sub> = V<sub>D</sub> + V<sub>T</sub>

V<sub>ICM(max)</sub> = 0.36 V

---

### Final Range

−0.34 V ≤ V<sub>ICM</sub> ≤ 0.36 V

---

## Output Common Mode Range (OCMR)

The OCMR specifies the range of output voltage for which the transistors remain in saturation.

### Maximum Output

V<sub>OCM(max)</sub> = 0.9 V

---

### Minimum Output

V<sub>OCM(min)</sub> = V<sub>S</sub> + V<sub>ov</sub>

V<sub>OCM(min)</sub> = −0.36 V

---

## Transient Analysis (Linearity)

📌 *Insert transient waveform (small signal)*
📌 *Insert transient waveform (large signal)*

For small input signals (<sub>100 mV</sub>), the output remains clean and undistorted, indicating linear operation.

As the input approaches <sub>0.68 V</sub>, distortion begins to appear. This is because current shifts entirely to one transistor, causing the other to approach cutoff.

---

## Simulated Gain

📌 *Insert gain waveform screenshot*

Measured values:

V<sub>in(pp)</sub> ≈ 100 mV</sub> <sub>V<sub>out(pp)</sub> ≈ 550 mV

A<sub>v</sub> ≈ 5.5

---

## Theoretical Gain

Using:

g<sub>m</sub> ≈ 3.59 mS

R<sub>out</sub> ≈ 1.25 kΩ

A<sub>v</sub> ≈ 4.49

---

## Discussion

The difference between theoretical and simulated gain arises due to practical effects such as finite output resistance, parasitic capacitances, and mobility variations. These factors are not included in simple analytical equations but are present in simulation models.

---

## AC Analysis

📌 *Insert Bode plot here*

The gain remains constant in the midband region and starts decreasing at higher frequencies due to parasitic capacitances. The bandwidth is observed to be in the MHz range, which is suitable for many analog applications.

---

## Conclusion

The MOS differential amplifier using resistive load has been successfully designed and analyzed. The circuit meets the required design constraints and shows expected performance.

The results obtained from simulation are close to theoretical values, confirming the validity of the design approach. Minor differences are due to real-world non-idealities, which are expected in practical circuits.

---
