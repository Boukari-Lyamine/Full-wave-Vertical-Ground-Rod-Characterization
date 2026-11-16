# Full-wave vertical ground rod characterization: data

Numerical data behind the article

L. Boukari and A. Bayadi, "When Is the Quasi-Static Image Enough? Validity Map and Accurate Sommerfeld Evaluation for Vertical Ground Rods", submitted.

All values were computed with one Python chain: the exact thin-tube kernel, the head–tail evaluator of the Sommerfeld remainder with the quasi-static part subtracted in closed form, and a Galerkin moment-method solver. The NEC-4.2 comparisons were run under an individual license; only derived quantities are given here.

## Cases

| Code | Meaning |
|---|---|
| `L03`, `L30` | rod length 3 m or 30 m, radius 1.25 cm, top at the surface |
| `s1e-3`, `s1e-2`, `s1e-1` | soil conductivity 10⁻³, 10⁻² or 10⁻¹ S/m, ε_r = 10 (1000, 100, 10 Ω m) |
| `_t05` | rod top buried at 0.5 m |
| `FD1e-3` | frequency-dependent soil of Alipio and Visacro, σ₀ = 10⁻³ S/m |

The four reference rods (`L03`/`L30` × `s1e-3`/`s1e-1`) are those of Figs. 2 and 3 of Honarbakhsh et al., IEEE Trans. EMC 63(1), 2021.

## Remainder variants

`exact`: the Sommerfeld remainder g_s. `static`: g_s replaced by τ/R_i. `phase`: g_s replaced by τ g_im. `zero`: g_s = 0. Here τ = 2ε̂_a/(ε̂_a + ε̂_g) is the interface weight of Eq. (6) of the article. `dZ_open` is the open-circuit term −j k_g/(2πσ) of Eq. (10).

## Files

| File | Content | In the article |
|---|---|---|
| `gs_reference_values_on_wire.csv` | g_s on the wire from a 25-digit reference, and the relative error of the evaluator (with and without subtraction) and of the two quasi-static substitutes | Tables 2 and 3 |
| `convergence_and_table5.csv` | Z_in and rod-top potential V_0 against the number of segments N, used for the Richardson extrapolation | Tables 4 and 5 |
| `zin_sweeps_all_cases.csv` | Z_in from 10 Hz to 30 MHz for every case and remainder variant, with the open-circuit term | Figs. 6 and 9, Table 6 |
| `digitised_honarbakhsh2021.csv` | \|Z_in\| read (digitized) from the published MoM and FEKO curves (Figs. 2 and 3 of Honarbakhsh et al. 2021) | Figs. 6 and 8, Table 5 |
| `nec42_rods_derived.csv` | difference between the NEC-4.2 rod current and ours (maximum and rms, relative to I_0) and the ratio of the rod-top potentials computed from the two currents | Figs. 7 and 8, Table 5 |
| `nec42_rods_terminal_and_lead.csv` | DC resistance seen at the NEC port and the change of the NEC current when the horizontal lead is raised from 0.2 to 1.5 m | Section VII-A |
| `permittivity_check.csv` | Z_in with the exact remainder and the relative change of Z_in for each substitute, for ε_r = 4, 30 and 80 (3 and 30 m rods, 1000 and 100 Ω m, 1 kHz to 30 MHz) | Section VIII |
| `gpr_iec62305.csv` | peak ground potential rise per kA, time to peak and impulse coefficient under the three IEC 62305-1 strokes, for every variant | Fig. 10, Table 7 |

Units are in the column names (`_ohm`, `_Hz`, `_m`, `_us`, `kV_per_kA`). Impedances are given as real and imaginary parts, with the e^{jωt} convention. In `convergence_and_table5.csv` the rows with `N = extrapolated` give the Richardson-extrapolated Z_in; their V_0 columns are left empty.

## NEC-4.2

The NEC runs use the Sommerfeld ground option (GN 3). NEC needs a closed circuit, so each rod sits in a fall-of-potential arrangement: a lead rises 0.5 m from the rod top to a horizontal lead 0.5 m above the ground, which runs to an identical return rod 120 m away (3 m rods) or 600 m away (30 m rods), with the source in the middle of the horizontal lead. The models were run at 51 frequencies from 100 Hz to 10 MHz. Both rod currents, NEC's and ours, are sampled at the NEC segment centers and normalized by the same linear extrapolation to the rod top before they are compared. No NEC input decks, raw outputs or program files are included.

## Code

The solver is not publicly available.

## License

Copyright (c) 2026 Lyamine Boukari. The data and this README are licensed under the Creative Commons Attribution 4.0 International License (CC BY 4.0); see `LICENSE` and https://creativecommons.org/licenses/by/4.0/. You may share and adapt them for any purpose, provided you cite the article and this repository. The values in `digitised_honarbakhsh2021.csv` were read from figures published by Honarbakhsh et al. (2021); cite that article as well when you use them.

## Citation

If you use these data, please cite the article (reference to be updated on publication) and this repository.

The repository itself can be cited as:

L. Boukari, "Full-wave vertical ground rod characterization: data," GitHub repository, 2026. [Online]. Available: https://github.com/Boukari-Lyamine/Full-wave-Vertical-Ground-Rod-Characterization

## Contact

Lyamine Boukari, Laboratoire d'Automatique de Sétif (LAS), Department of Electrical Engineering, Faculty of Technology, Setif 1 University-Ferhat Abbas, Setif, 19000, Algeria. l_boukari@univ-setif.dz
