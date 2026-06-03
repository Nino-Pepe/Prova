
#### On Windows:

Open the Powershell, then verify if OpenSSH is already installed:

```
ssh -V
```

Now generate the key (suggested: Ed25519):

```
ssh-keygen -t ed25519 -C "info/commento sulla chiave creata"
```

The system will ask to you in which path you want to save the key, press Enter to use the default path.
After, the system will ask to you to insert a strong passphrase used to open and read the private key.

The key will be saved in this path: 

```
C:\Users\<YOUR_USER>\.ssh\
```

You will find this two keys:
- id_ed25519: that's your private key, you don't never share this one.
- id_ed25519: that's your public key, you can share this with the device you need to connect with ssh method.

Look for the permissions of the private key, it needs to have access only from:
- Your user
- SYSTEM

No one else.

##### Use ssh-agent (Optional):

If you don't want to write your passphrase any time.
Look for the service if is up.

```
Get-Service ssh-agent
```

Set the service in a "Manual" or "Automatic" way to start:

```
Set-Service -Name ssh-agent -StartupType Manual
```

Change the StartupType if u want the Automatic start when the system goes on.

Now you can start the service:

```
Start-Service ssh-agent
```

Add your ssh-key:

```
ssh-add $env:USERPROFILE\.ssh\id_ed25519
```

Looks on the list of the added keys:

```
ssh-add -l
```

Enjoy.
