---
title: Two Electron Coulomb Integral
date: 2024-03-14 12:00:00
tags: density fitting
categories: [Basic, Integral]
mathjax: true
---
### Four-Center Two-Electron Coulomb Integral

## Directory Structure

- `df_hf_int`: Directory where the three-center two-electron integrals are saved.
- `V_0.h5`: HDF5 file containing the three-center two-electron intagrals.

## Integrals Definition

### Chemist's Notation
In **chemist's notation**, the integral is represented as
$$
\begin{equation}
U_{ijkl} = (ij\vert kl) = \int\int dr_1 dr_2 \phi^*_i(r_1)\phi_j(r_1)\frac{1}{\vert r_1-r_2\vert}\phi^*_k(r_2)\phi_l(r_2)
\end{equation}
$$
- **Function**: `chem_four_center_integral` computes this integral.
- Used for scGW
### Physicist's Notation
In **physicist's notation**, the integral is defined as
$$
\begin{equation}
V_{ijkl} = \langle ij\vert kl\rangle =  \int\int dr_1 dr_2 \phi^*_i(r_1)\phi_j^*(r_2)\frac{1}{\vert r_1-r_2\vert}\phi_k(r_2)\phi_l(r_1) 
\end{equation}
$$
- **Function**: `phys_four_center_integral` computes this integral.
- Used for GF2
### Simplification through Density Fitting
The expression for $U_{ijkl}=\sum_{Q} V_{ij}(Q)V_{kl}(Q)$ and $V_{ijkl}=\sum_{Q} V_{il}(Q)V_{jk}(Q)$ suggests a simplification technique known as density fitting or resolution of the identity (RI), where the complex four-center integrals are approximated using a sum over simpler terms involving fewer centers. This approach significantly reduces computational cost.
$$
\begin{equation}
V_{ij}(Q) = (ij\vert Q) = \int \int dr_1dr_2 \phi_i(r_1) \phi_j(r_1) \frac{1}{\vert r_1-r_2\vert}\chi_{Q}(r_2)
\end{equation}
$$

## Usage
Read the integrals from `df_hf_int`
```python
V_Qij = read_integrals(path_to_df)
```
Compute the coulomb integral in chemist's notation, $U_{ijkl}$
```python
U_ijkl = chem_four_center_integral(V_Qij)
```
Compute the coulomb in physicist's notation, $V_{ijkl}$
```python
V_ijkl = phys_four_center_integral(V_Qij)
```
