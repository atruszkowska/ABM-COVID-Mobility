# ABM-COVID-DSL
High-resolution agent-based model of COVID-19 with testing, treatment, and human mobility

## Code structure

Details about the code and usage examples can be found in the documentation, and the manual.

The directories are as follows: 
- `include` - header files
- `src` - source files
- `scripts` - python scripts for general use throughout the repository
- `tests` - tests developed for this code
- `parameters` - data and scripts for fitting of some of the parameters
- `simulations` - simulations, specifically,
	- `complete_var_reopening_study` - simulations with fixed vaccination rate and variable reopening rates
	- `complete_two_rates_study` - parametric studies of a series of vaccination and reopening rates
The simulation groups have three variants for different testing efficacies. These simulations are set up and ran automatically using welll-commented make_and_run.sh scripts in each subdirectory. Before running, adjust the number of simulations ran simultanously according to your own resources.

## Compiling and running

Complete compilation scripts are written in Python and can be found in subdirectories of `simulations`. They are executed by running

```bash 
python3.X compilation.py
```
in the terminal. 

The code was developed and tested on MacOS and Linux, some of its parts may not be compatible with Windows.

Compiler requirement is availability of the C++11 standard. Python version used througout the development was 3.6 and 3.8, other 3.X version should work as well. 

## Tests

All the core and most of the side functionality of the code is extensively tested, with tests present in th `tests` directory. Each testing directory has its own python script that compiles  and exectues all its tests. The test outcomes are printed to the screen and pass/fail are color-coded and clearly indicated. To run all of the tests execute: 

```bash
python3.X run_all_tests.py 
```
in the `tests` directory. Some of the tests may at times fail due to insufficient statistical sampling (e.g. in distribution tests).

## Documentation

The documentation is generated with [Doxygen](https://www.doxygen.nl/index.html). To create your own, run `doxygen Doxyfile` in the root (this) directory. 

## Notes

- Current simulation wrappers and drivers are written in MATLAB. Python versions will soon be available.
- To run the wrappers with MATLAB on older Linux systems one may need to manually specify the location of `libstdc++` library. General instructions are available through [this post](https://stackoverflow.com/a/58219652/2763915). Specifically, on a `Red Hat Enterprise Linux Workstation release 7.3 (Maipo)` the command sequence was:

```bash
locate libstdc++
export LD_PRELOAD=/usr/lib64/libstdc++.so.6.0.19
```
We encourage the users and developers to report any issues, including platform incompatibility and failed tests on our GitHub page or directly, by sending us an email.  

## Citation

If you find this software useful, consider citing

*Truszkowska, A., Thakore, M., Zino, L., Butail, S., Caroppo, E., Jiang, Z.P., Rizzo, A. and Porfiri, M., 2021. Designing the Safe Reopening of US Towns Through High‐Resolution Agent‐Based Modeling. Advanced theory and simulations, 4(9) p.2100157.*
