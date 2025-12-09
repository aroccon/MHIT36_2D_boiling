## 2D version of MHIT36
Version of MHIT36 simpliefied to work in 2D (single GPU version)
Numerical scheme: Finite difference-based (FD2).
Time integration:
- Temperature: SSP-RK3 
- Navier-Stokes: RK3
- Phase-field: RK3 (to be implemented)
- NS: Fractional method, Poisson solver based on FFT (along x - periodic) + TDMA (y, walls).


~~~text
███    ███ ██   ██ ██ ████████ ██████   ██████       
████  ████ ██   ██ ██    ██         ██ ██              
██ ████ ██ ███████ ██    ██     █████  ███████   
██  ██  ██ ██   ██ ██    ██         ██ ██    ██     
██      ██ ██   ██ ██    ██    ██████   ██████        
~~~


If you use this code, please cite the following works: 
```bibtex
  @article{roccon2025,
  title   = {MHIT36: A Phase-Field Code for Gpu Simulations of Multiphase Homogeneous Isotropic Turbulence},
  author  = {Roccon, A. and Enzenberger, L. and Zaza, D. and Soldati, A.},
  journal = {Computer Physics Communications},
  year    = {2025},
  volume  = {314},
  issue   = {109804},
  doi     = {https://doi.org/10.1016/j.cpc.2025.109804}
}
```

```bibtex
  @article{roccon2026,
  title   = {MHIT36: Extension to wall-bounded turbulence and scalar transport equation},
  author  = {Roccon, A.},
  journal = {Computer Physics Communications},
  year    = {2026},
  volume  = {---},
  issue   = {109956},
  doi     = {https://doi.org/10.1016/j.cpc.2025.109956}
}
```


## Check list of features implemented (or to be implemented)

- Poisson solver (Matlab) ✅
- Poisson solver validation (Matlab) ✅
- Poisson solver convergence (Matlab) ✅
- Poisson solver (Fortran: FFT forth and back) ✅
- Poisson solver (Fortran) ✅
- Added support for stretched nodes along z (Matlab only, easy to move in Fortan) ✅
- Introduced phi ✅ 
- Introduced temperature ✅ 
- Introduced temporal loop ✅ 
- Navier-Stokes solution ✅ 
- Validation (phi) ✅ 
- Validation (temp) ✅ 
- Validation (NS): Channel flow (pressure-driven + wall-driven) ✅
- RB setup ✅ 
- GPU offloading of entire code  ✅
- TDMA optimization (x 10 speed-up)  ✅

## Performance and resolution tested

- 512 x 256 - 2.5 ms/iter - RTX5000 16GB (NS + Temp exp. + phase-field)
- 512 x 256 - 0.7 ms/iter - A100 64GB (NS + Temp exp. + phase-field)
- 2048 x 1024 - 19 ms/iter - RTX5000 16GB (NS + Temp exp. + phase-field)
- 2048 x 1024 - 5.5 ms/iter - A100 64GB (NS + Temp exp. + phase-field)
- 4096 x 2048 - 70 ms/iter - RTX5000 16GB (NS + Temp exp. + phase-field)

## Grid points (staggered)

![Test](doc/grid.png)


