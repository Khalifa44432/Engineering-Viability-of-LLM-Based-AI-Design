# Analytical Instructions Provided to the LLM Agent  
*(Khalifa et al., 2025)*

The following analytical relationships were supplied to each agent as deterministic rules to generate valid coil and circuit parameters.

---

## Core Equations

**Skin Depth**  
\[
\delta = \frac{1}{\sqrt{\pi f_s \sigma \mu_0}}
\]

**DC Resistance**  
\[
R_{DC} = \frac{l}{\sigma \pi (w_t/2)^2}
\]

**AC Resistance**  
\[
R = R_{DC}\left(\frac{w_t}{4\delta}\right)
\]

**Inductance**  
\[
L = \frac{39.37\, N^2 (D_o - N(w_t + p))^2}{16 D_o + 28 N (w_t + p)}\;[\mu H]
\]

**Parasitic Capacitance**  
\[
C_p = 0.035\, D_o + 0.06\;[pF]
\]

---

## Compensation Topologies

**Series–Series (SS)**  \( C_1 = \frac{C_2 L_2}{L_1} \)  
**Series–Parallel (SP)**  \( C_1 = \frac{C_2 L_2^2}{L_1 L_2 - M^2} \)  
**Parallel–Parallel (PP)**  \( C_1 = \frac{(L_1 L_2 - M^2)\, C_2\, L_2^2}{(M^4 C_2 R / L_2) + (L_1 L_2 - M^2)^2} \)  
**Parallel–Series (PS)**  \( C_1 = \frac{C_2 L_2}{(M^4 / (L_1 L_2 C_2 R)) + L_1} \)

---

## Coupling, Resonance, Impedances

\[
M = k \sqrt{L_1 L_2}, \qquad f_r = \frac{1}{2\pi \sqrt{L_1 C_1}}, \qquad \omega = 2\pi f_r
\]

\[
Z_1 = R_1 + R_s + j\omega L_1 + \frac{1}{j\omega C_1}, \qquad
Z_2 = R_L + R_2 + j\omega L_2 + \frac{1}{j\omega C_2}
\]

**Capacitance from L and \(f_r\)**  
\[
C = \frac{1}{(2\pi f_r)^2 L}
\]

**Quality Factor**  
\[
Q = \frac{\omega (L - C_p R^2 - C_p L^2 \omega^2)}{R}
\]

**Maximum Efficiency (identical coils \(Q_1=Q_2=Q\))**  
\[
\eta_{\max} = \frac{k^2 Q^2}{\left(1 + \sqrt{1 + k^2 Q^2}\right)^2}
\]
