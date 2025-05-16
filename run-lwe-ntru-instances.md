# Make sure to activate the G6K environment:
```console
source ./activate
```


## To run lwe instance:
for dimension n and width alpha, run the following command:  
```console
python3 lwe_challenge.py n --lwe/alpha alpha
```

### To specify the sieving algorithm to be used:
```console
python3 lwe_challenge.py n --lwe/alpha alpha --lwe/sievealg bdgl
```
Options are default=hk3 and guass, nv, bgj1 and bdgl.

###bkz_fpylll-crossover  
```console
python lwe_challenge.py 50 --lwe/alpha 0.020 --bkz/fpylll-crossover 61 
```

## To run NTRU HPS instance:
### To compute with fpylll enumeration, run the following command:
```console
python3 attack_ntru.py HPS n -q=q --threads=64 --verbose=True
```
### To compute with lattice sieving, run the following command:
```console
python3 attack_ntru.py HPS n -q=q --bkz_alg=pump_n_jump --threads=64 --verbose=True
```
## To run NTRU HRSS instance:
### To compute with fpylll enumeration, run the following command:
```console
python3 attack_ntru.py HRSS n --threads=64 --verbose=True
```
### To compute with lattice sieving, run the following command:
```console
python3 attack_ntru.py HRSS n --bkz_alg=pump_n_jump --threads=64 --verbose=True
```
