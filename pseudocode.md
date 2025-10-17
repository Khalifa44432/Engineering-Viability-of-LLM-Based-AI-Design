## Algorithm 1 — LLM-Based WPT Design, Validation, and Prototyping (Khalifa et al., 2025)

**Inputs:** Objectives & Constraints (O&C_D), Specifications/Requirements (SP/R), Target Efficiency (η_WPT,target)  
**Outputs:** Validated prototype-ready WPT design

```
1   prompt ← (O&C_D, SP/R, η_WPT,target)
2   designs ← LLM_generate(prompt, data_sources = {IEEE, Scopus, Textbooks})

3   // --- First Stage: Analytical (Mathematical) Validation ---
4   valid_candidates ← ∅
5   for each design d in designs do
6       extract d → (N, δ, D_o, w, R_DC, R_AC, L, C_p, Q, k, P, η_max,theoretical, coil_type)
7       if satisfies(d, O&C_D, SP/R) then
8           add d to valid_candidates
9       end if
10  end for
11  BestDesign ← select_best(valid_candidates)     // selection per stated objectives (e.g., η_max,theoretical, k, bounds)
12  if BestDesign == None then
13      prompt_again(O&C_D, SP/R)                  // refine and regenerate
14      stop
15  end if

16  // --- Second Stage: Simulation Validation ---
17  PSIM_results  ← simulate_system(BestDesign)    // {I_primary, V_primary, I_secondary, V_secondary, η_WPT}
18  ANSYS_results ← simulate_coil(BestDesign)      // {H, d, k, B_max, B_vector}
19  S ← compare_to_targets(PSIM_results, ANSYS_results, O&C_D, SP/R)

20  if S meets (O&C_D, SP/R) then
21      // --- Prototype Development ---
22      HFAC_inverter ← build_inverter(BestDesign)
23      coils        ← fabricate_coils(BestDesign)
24
25      // --- Proceed to Experimentation ---
26      measurements ← lab_tests(HFAC_inverter, coils)     // {η_exp, waveforms, thermal}
27      archive(BestDesign, PSIM_results, ANSYS_results, measurements)
28      return final_report(BestDesign, measurements)
29  else
30      prompt_again(O&C_D, SP/R)                  // feedback loop per workflow figure
31      stop
32  end if
```
