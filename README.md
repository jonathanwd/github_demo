# User Password Retreival From Memory Dump

## Download and Install Windows 7 Virtual Machine
* Windows 7 VMs can be downloaded from Microsoft at https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/. 
These instuctions were tested on the "IE11 on Win7 (x86)" VM.
* Install the VM on the platform of your choice. These VMs expire after 90 days, so Microsoft recommends creating a snapshot after the initial installation. 
You may need to restart the VM after installation. 

## Download Volatility
* Volatility can be downloaded from http://downloads.volatilityfoundation.org/releases/2.6/volatility_2.6_win64_standalone.zip.
* Save the zip file onto the VM and extract its contents.

## Download DumpIt
* Downloading DumpIt requires an account from https://my.comae.com/. Comae accounts are free for personal non-commercial use. 
* Once you have created an account, DumpIt can be downloaded from https://my.comae.com/tools/.
* Save the zip file onto the VM and extract the contents. 

## Obtain Memory Image Using DumpIt
* Open a command prompt on the VM.
* Navigate to the folder containing "DumpIt.exe".
* Run DumpIt: `DumpIt.exe /OUTPUT image.dmp`

## Retrieve Password Using Volatility
* Copy the memory image "image.dmp" to the folder containing "volatility_2.6_win64_standalone.exe".
* To retrieve the password you will need to know the volatility profile (the profile is based on the operating system and service pack version, it should be "Win7SP1x64" for the "IE11 on Win7" VM).

### Dump Registry Hives
* Run  `volatility_2.6_win64_standalone.exe -f image.dmp --profile=Win7SP1x64 hivelist` to see the registry hive offsets.
* We will need the SYSTEM (-y) and SAM (-s) virtual offests.

### Dump Password Hashes
* Run `volatility_2.6_win64_standalone.exe -f image.dmp --profile=Win7SP1x64 hashdump -y 0xfffff8a000024010 -s 0xfffff8a00278c010 > hashes.txt` to dump the password hashes.
* View the hashes in the command prompt: `type hashes.txt`
* Copy the hashes to https://crackstation.net/ to crack the passwords (the NTLM hash is the part between the third colon and the final three colons).

## References
* https://www.aldeid.com/wiki/Volatility/Retrieve-password
