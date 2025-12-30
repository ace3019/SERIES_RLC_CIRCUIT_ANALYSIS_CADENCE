# SERIES_RLC_CIRCUIT_ANALYSIS_CADENCE
This project explores the design and simulation of a Series RLC Resonance Circuit using Cadence Virtuoso IC617. It validates the theoretical resonant frequency through S-parameter and AC analyses.
# Comprehensive Analysis of Series RLC Resonance | Cadence Virtuoso IC617

This repository presents a detailed analysis of a **Series RLC Resonance Circuit**, designed and simulated using **Cadence Virtuoso IC617**. The project rigorously validates theoretical predictions against Spectre-based S-Parameter and AC analyses, focusing on resonant frequency, impedance matching, and frequency response.

---

## 1. Theoretical Framework
A series RLC circuit exhibits resonance when the inductive reactance ($X_L$) and capacitive reactance ($X_C$) are equal, leading to a purely resistive input impedance at the resonant frequency ($f_0$).

### Governing Equations
* **Resonant Frequency ($f_0$):**
    $$f_0 = \frac{1}{2\pi\sqrt{LC}}$$
* **Input Impedance ($Z_{in}$):**
    $$Z_{in}(f) = R + j\left(2\pi fL - \frac{1}{2\pi fC}\right)$$
* **Reactance Components:**
    $$X_L = 2\pi fL \quad \text{and} \quad X_C = \frac{1}{2\pi fC}$$

Theoretical RLC Circuit<img width="845" height="388" alt="Screenshot 2025-08-05 033418" src="https://github.com/user-attachments/assets/82c159b1-7ca5-4c3c-a1b4-06410f399126" />

*Figure 1: Basic Series RLC circuit and the formula for resonant frequency.*



Input Impedance Equation<img width="1916" height="1022" alt="Screenshot 2025-08-05 033443" src="https://github.com/user-attachments/assets/c8495292-903c-4584-b33b-f6d3cbbb6646" />

*Figure 2: Input impedance formula illustrating the reactive components.*

---

## 2. Design and Implementation

### Schematic Capture
The RLC circuit was created in the **Virtuoso Schematic Editor L**. It consists of a $50\text{ }\Omega$ port (representing the source) in series with a resistor, capacitor, and inductor.

Circuit Schematic in Virtuoso<img width="950" height="909" alt="Screenshot 2025-08-05 034749" src="https://github.com/user-attachments/assets/67764876-7e93-446b-aafd-fc2c53870a3b" />

*Figure 3: Schematic diagram of the series RLC circuit in Cadence Virtuoso.*

### Design Variables
The component values were defined as variables in the **Analog Design Environment (ADE L)** for easy modification and parametric sweeps.

| Variable | Description | Value |
| :------- | :---------- | :---- |
| **C** | Capacitance | $3\text{ pF}$  |
| **L** | Inductance  | $10\text{ nH}$ |
| **R** | Resistance  | $50\text{ }\Omega$ |
| **Rs** | Source Resistance | $50\text{ }\Omega$ |

ADE L Design Variables Setup<img width="945" height="953" alt="Screenshot 2025-08-05 034910" src="https://github.com/user-attachments/assets/09f5f883-03bb-4cf5-b880-2f94e315ab1b" />

*Figure 4: ADE L window showing the defined design variables.*

---

## 3. Simulation Setup

### Analysis Configuration (ADE L)
**S-Parameter (sp) Analysis** was selected to determine the return loss ($S_{11}$) and frequency response.
* **Sweep Variable:** Frequency
* **Start Frequency:** $1\text{ MHz}$
* **Stop Frequency:** $2\text{ GHz}$
* **Sweep Type:** Linear with a step size of $10\text{ kHz}$

SP Analysis Configuration<img width="957" height="979" alt="Screenshot 2025-08-05 035030" src="https://github.com/user-attachments/assets/c8b25e6d-6821-4916-86bf-dcb4a4bb4e21" />

*Figure 5: Configuration of S-Parameter analysis in ADE L.*

### Output Saving Options
To enable comprehensive post-simulation analysis, all signals, power levels, and currents were explicitly saved.

| Option                     | Setting |
| :------------------------- | :------ |
| **Save signals to output** | all     |
| **Save power signals** | all     |
| **Save current devices** | all     |
| **Save AC terminal currents** | yes |

Save Options Window<img width="949" height="990" alt="Screenshot 2025-08-05 042526" src="https://github.com/user-attachments/assets/b9c67595-031d-472b-8a22-af4d14ae20bf" />

*Figure 6: "Save Options" window in Cadence, configured for detailed output saving.*

### Plotting Outputs
The **Direct Plot Form** was used to plot $S_{11}$ in dB20 (Return Loss) directly from the simulation results.

Direct Plot Form<img width="951" height="950" alt="Screenshot 2025-08-05 035348" src="https://github.com/user-attachments/assets/2933a597-e8db-4b43-895a-e689330c1ed3" />

*Figure 7: Direct Plot Form setup for plotting S11 in dB20.*

---

## 4. Results Section

### Measured Parameters Summary
The simulation results precisely validate the theoretical resonant frequency and optimal impedance matching.

| Parameter                      | Theoretical Value | Simulated Value     | Observation                                     |
| :----------------------------- | :---------------- | :------------------ | :---------------------------------------------- |
| **Resonant Frequency ($f_0$)** | $918.88\text{ MHz}$  | $918.88\text{ MHz}$   | Exact match, validating component selection.    |
| **Minimum $S_{11}$ (Return Loss)** | $-\infty\text{ dB}$ | $-114.538\text{ dB}$ | Near-perfect impedance matching to $50\text{ }\Omega$. |
| **Input Impedance ($Z_{in}$)** | $50\text{ }\Omega$   | $50\text{ }\Omega$    | Purely resistive at resonance.                  |

### S-Parameter Response ($S_{11}$)
The $S_{11}$ plot shows a deep null at the resonant frequency, demonstrating the circuit's excellent impedance matching and filtering capabilities.

S11 Resonance Plot<img width="952" height="949" alt="Screenshot 2025-08-05 040228" src="https://github.com/user-attachments/assets/0ebea788-e994-44fe-95ed-de571d8c4106" />

*Figure 8: S11 plot showing a deep null at 918.88 MHz, indicating resonance.*

### Input Impedance ($Z_{11}$)
The combined plot of $S_{11}$ and the real part of $Z_{11}$ confirms that at resonance, the input impedance becomes purely resistive and matches the $50\text{ }\Omega$ resistance.

S11 and Z11 Plot<img width="933" height="783" alt="Screenshot 2025-08-05 040518" src="https://github.com/user-attachments/assets/4c939c7d-4631-4311-baf1-3f7ba3c912b5" />

*Figure 9: Combined plot of S11 and the real part of Z11, showing 50 Ohms at resonance.*

### AC Current Response
The AC sweep shows the current magnitude peaking at resonance. This confirms the band-pass behavior of the matching network.
* **Peak Current:** 10.0 mA
* **Resonant Frequency:** 919.13 MHz

AC Current Plot<img width="1565" height="1008" alt="Screenshot 2025-08-05 043133" src="https://github.com/user-attachments/assets/125925c6-be1d-4229-b4ac-12c6dd85595b" />

### Power & Performance Dashboard
This dashboard correlates Current, Impedance, and Power. Note that peak power delivery aligns with the current peak, ensuring the circuit operates efficiently at the target frequency.
* **Peak Power:** 5.0 mW
* **Frequency Range:** 0.5 GHz - 1.5 GHz

Performance Dashboard<img width="1889" height="946" alt="Screenshot 2025-08-05 043321" src="https://github.com/user-attachments/assets/b74f45ad-f984-44b1-a200-0f685881a33f" />



---

## 5. Conclusion
This project successfully demonstrated the design, simulation, and analysis of a series RLC resonance circuit in Cadence Virtuoso. The simulated resonant frequency of $918.88\text{ MHz}$ and the exceptionally low return loss of $-114.538\text{ dB}$ validate the theoretical models and showcase precise impedance matching. The comprehensive simulation setup, including detailed save options, provides a robust methodology for characterizing high-frequency passive components, applicable in analog filter design and system-level performance optimization.

---

## 6. Future Work
1.  **Quality Factor (Q) Analysis:** Calculate the Q-factor of the resonator from the bandwidth of the $S_{11}$ curve to further characterize its selectivity.
2.  **Parametric Sweep:** Conduct a parametric sweep on L and C values to observe their impact on the resonant frequency and Q-factor.
3.  **Temperature Analysis:** Perform AC analysis across varying temperatures to study the stability of the resonant frequency.
4.  **Noise Analysis:** Evaluate the noise performance of the RLC circuit.
5.  **Layout Design:** Progress to physical layout design and post-layout simulation to account for parasitic effects.

---

## 7. Tools Used
* **Cadence Virtuoso IC617**
* **Spectre® Simulation Platform**
* **Virtuoso® Visualization & Analysis XL**

### Author : Shashvat Mishra, BTech VLSI,Punjab Engineering College
