Refer setup file to setup G6K for solving LWE and NTRU instances.  
After Editing the **bootstrap.sh** file in G6K, run the following command to create g6k environment and install fplll, fpylll:
```console
./bootstrap.sh [-j #]
```
  
This will build fpylll and all the dependencies.  
We might need to manually install mod, sympy to solve lwe-instances.  
Use the following command to install these in the G6K environment,
```console
pip install mod sympy
```

After setting up the G6K environment, copy ntru-with-sieving files into the G6K folder.
Then, we can run ntru-instances using G6K using the commnad mentioned in run-lwe-ntru-instances file.
