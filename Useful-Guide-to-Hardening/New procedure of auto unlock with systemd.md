
Install the tools you needs to configure your system: 

```
sudo apt install tpm2-tools
```

Look for the crypted disk:

```
lsblk -f
```

Then:

```
sudo systemd-cryptenroll --tpm2-device=auto --tpm2-pcrs=7+11+14 /dev/nvme0n1p3
```

Pay attention, you need too change the path of the device with the crypted one, sure it can be different from this. 

Verify with:

```
sudo systemd-cryptenroll /dev/nvme0n1p3
```

You will see something like this:

```
tpm2: yes
or
o password
1 tpm2
```

In some OS (Ubuntu in particular) you need to rebuild the initramfs:

```
sudo update-initramfs -u
```

Reboot the system. 
Enjoy. 