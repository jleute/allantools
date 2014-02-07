allantools
==========

A small Python library for calculating Allan deviation and related statistics.

Input data should be evenly spaced observations of either fractional frequency,
or phase in seconds. Deviations are calculated for given tau values in seconds.

Usage:
```python
import allantools # https://github.com/aewallin/allantools/
rate = 1/float(data_interval) # data rate in Hz
taus = [1,2,4,8,16] # tau-values in seconds
# fractional frequency data
(taus_used, adev, adeverror, adev_n) = allantools.adev(fract_freqdata, rate, taus)
# phase data
(taus_used, adev, adeverror, adev_n) = allantools.adev_phase(phasedata, rate, taus)

# notes:
#  taus_used may differ from taus, if taus has a non-integer multiples of data_interval
#  adeverror assumes 1/sqrt(adev_n) errors
```

These statistics are currently included:
* ADEV    Allan deviation
* OADEV   overlapping Allan deviation,
* MDEV    modified Allan deviation,
* TDEV    Time deviation
* HDEV    Hadamard deviation
* OHDEV   overlapping Hadamard deviation
* TOTDEV  Total deviation
* MTIE    Maximum time interval error
* TIERMS  Time interval error RMS

see /tests for tests that compare allantools output to other programs.

No profiling or optimization attempt was made. Patches that give speedups are welcome.
Make sure your patch does not break any of the tests, and does not significantly reduce the readability of the code.
