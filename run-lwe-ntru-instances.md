## To run lwe instance:
for dimension n and width alpha, run the following command:  
```console
python3 lwe_challenge.py n --lwe/alpha alpha
```
bkz_fpylll-crossover  
```console
python lwe_challenge.py 50 --lwe/alpha 0.020 --bkz/fpylll-crossover 61 --sieve gauss_triple_mt --db-size-base 1.1547005383792515
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
