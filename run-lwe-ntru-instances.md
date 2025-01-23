## To run lwe instance:
for dimension n and width alpha, run the following command:  
```console
python3 lwe_challenge.py n --lwe/alpha alpha
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
