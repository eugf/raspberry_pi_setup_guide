This part is specifically for Genspace NYC's OpenPlant group, and it assumes you have the hardware all setup and connected (Rpi0 + PCB + camera + LED's).
This will then install the software needed to operate aforementioned components. 

SSH onto your Rpi0 and run this command:

```
pip3 install git+https://github.com/genspace/openplant-incubator -U
```

Then run 
```
incubate-me
```

You will need to get a password from the Genspace NYC's OpenPlant group to access the AWS server

If you need to upgrade the script, run this command:
```
pip3 install --upgrade git+https://github.com/genspace/openplant-incubator.git
```
