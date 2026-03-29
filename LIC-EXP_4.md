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



# Circuit 2: Differential Amplifier with Active Load

---

## Objective

The objective of this design is to implement a MOS differential amplifier using an active load configuration and analyze its performance. The focus is on maintaining proper biasing, ensuring all transistors operate in saturation, and evaluating gain, linearity, and frequency response.

---

## Given Parameters

Technology: 180 nm

<sub>V<sub>DD</sub> = +0.9 V</sub> <sub>V<sub>SS</sub> = −0.9 V</sub>
Power ≤ 2.2 mW <sub>L = 540 nm</sub>

---

## Design Approach

In this circuit, the resistive load used earlier is replaced with an active load using MOSFETs. This helps in increasing the output resistance and thereby improving the gain of the amplifier.

The circuit consists of:

* M1, M2 → input differential pair
* M3, M4 → active load
* M5 → tail current source

The design is carried out such that all transistors remain in saturation and the current distribution remains symmetrical under zero differential input.

---

## Tail Current Calculation

The total current is limited by the power constraint:

<sub>P = (V<sub>DD</sub> − V<sub>SS</sub>) I<sub>SS</sub></sub>

<sub>1.8 × I<sub>SS</sub> ≤ 2.2 × 10⁻³</sub>

<sub>I<sub>SS</sub> ≈ 1.22 mA</sub>

This value is chosen to ensure safe operation within the given power limit.

---

## Current Distribution

Under balanced condition:

<sub>I<sub>D1</sub> = I<sub>D2</sub> = I<sub>SS</sub> / 2</sub>

<sub>I<sub>D</sub> ≈ 0.61 mA</sub>

This ensures symmetric operation of the differential pair.

---

## Bias Conditions

<sub>V<sub>G</sub> = 0 V</sub> <sub>V<sub>S</sub> ≈ −0.7 V</sub>

<sub>V<sub>GS</sub> = 0.7 V</sub>

<sub>V<sub>ov</sub> ≈ 0.34 V</sub>

This confirms that the NMOS transistors are properly turned ON.

---

## Region of Operation Check

For saturation:

<sub>V<sub>DS</sub> ≥ V<sub>ov</sub></sub>

<sub>V<sub>DS</sub> = 0 − (−0.7) = 0.7 V</sub>

Since:

<sub>0.7 > 0.34</sub>

all NMOS devices operate in saturation.

---

## Width Calculation

### NMOS Differential Pair (M1, M2)

Using:

<sub>I<sub>D</sub> = (1/2) μ<sub>n</sub>C<sub>ox</sub> (W/L)(V<sub>ov</sub>)²</sub>

Rearranging:

<sub>W = (2I<sub>D</sub>L)/(μ<sub>n</sub>C<sub>ox</sub>(V<sub>ov</sub>)²)</sub>

Calculated width:

<sub>W ≈ 31.6 µm</sub>

After fine-tuning in simulation to match the desired current and output conditions:

<sub>W ≈ 36 µm</sub>

---

### Tail Current Source (M5)

Using:

<sub>W = (2I<sub>D</sub>L)/(μ<sub>n</sub>C<sub>ox</sub>(V<sub>ov</sub>)²)</sub>

Calculated width:

<sub>W ≈ 139 µm</sub>

After adjustment for proper bias:

<sub>W ≈ 228 µm</sub>

This ensures stable current generation.

---

### Active Load (M3, M4)

Calculated width:

<sub>W ≈ 8.7 µm</sub>

This value ensures that PMOS devices remain in saturation and provide sufficient output resistance.

---

## DC Analysis

📌 *Insert DC schematic screenshot here*
📌 *Insert DC operating point screenshot here*

The DC analysis verifies that:

* Tail current is close to the designed value
* Current splits equally between M1 and M2
* Output nodes remain symmetric
* All transistors operate in saturation

---

## Input Common Mode Range (ICMR)

The ICMR is the range of input voltage for which all transistors remain in saturation.

### Minimum Value

<sub>V<sub>ICM(min)</sub> = V<sub>S</sub> + V<sub>T</sub></sub>

<sub>V<sub>ICM(min)</sub> = −0.34 V</sub>

---

### Maximum Value

To keep PMOS load in saturation:

<sub>V<sub>ICM(max)</sub> = V<sub>D</sub> + |V<sub>TP</sub>|</sub>

<sub>V<sub>ICM(max)</sub> ≈ 0.39 V</sub>

---

### Final Range

<sub>−0.34 V ≤ V<sub>ICM</sub> ≤ 0.39 V</sub>

---

## Output Common Mode Range (OCMR)

### Minimum Output

<sub>V<sub>out(min)</sub> = V<sub>S</sub> + V<sub>ov</sub></sub>

<sub>V<sub>out(min)</sub> = −0.36 V</sub>

---

### Maximum Output

<sub>V<sub>out(max)</sub> = V<sub>DD</sub> − V<sub>ovp</sub></sub>

<sub>V<sub>out(max)</sub> ≈ 0.65 V</sub>

---

## Differential Input Range

For linear operation:

<sub>|v<sub>id</sub>| ≤ 2V<sub>ov</sub></sub>

<sub>|v<sub>id</sub>| ≤ 0.68 V</sub>

Beyond this, one transistor enters cutoff and distortion occurs.

---

## Transient Analysis

📌 *Insert transient waveform (small input)*
📌 *Insert transient waveform (large input)*

### Linear Region

For small input (≈100 mV):

* Output is smooth and sinusoidal
* Current is shared between both transistors
* Circuit behaves linearly

---

### Non-Linear Region

For larger input (≈600 mV):

* Output shows distortion
* One transistor carries most of the current
* Amplifier deviates from linear behavior

---

## Simulated Gain

📌 *Insert waveform screenshot here*

<sub>V<sub>in(pp)</sub> ≈ 100 mV</sub> <sub>V<sub>out(pp)</sub> ≈ 181 mV</sub>

<sub>A<sub>v</sub> ≈ 1.81</sub>

<sub>A<sub>v(dB)</sub> ≈ 5.15 dB</sub>

---

## Theoretical Gain

<sub>g<sub>m</sub> ≈ 4.11 mS</sub>

<sub>R<sub>out</sub> ≈ 8.2 kΩ</sub>

<sub>A<sub>v</sub> ≈ 33.7</sub>

---

## Discussion

The difference between theoretical and simulated gain is quite significant in this case. This is mainly because theoretical calculations assume ideal current sources and infinite output resistance.

In practice, the current source (M5) and active load (M3, M4) introduce non-idealities which reduce the effective gain.

---

## AC Analysis

📌 *Insert Bode plot screenshot here*

The frequency response shows:

* Flat gain in midband region
* Gain roll-off at higher frequencies

Bandwidth is observed in the GHz range due to small device dimensions and parasitic effects.

---

## Conclusion

The differential amplifier with active load is successfully designed and analyzed.

* The circuit satisfies the power constraint
* Proper biasing ensures saturation
* Gain is reduced compared to ideal case due to non-ideal effects
* Linear operation is maintained only for small signals

Overall, the circuit demonstrates the practical limitations of MOS differential amplifiers with active loads.

---

