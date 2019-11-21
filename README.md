# github_demo

## Create Windows VM
### Download Windows Image
https://www.microsoft.com/software-download/windows10
#### Windows Installation 
If you downloading the image on a Windows machine, you will use a download tool. (The Microsoft Media Creation Tool).
Create installation media for another PC.
I don't have a product key
Custom Install Windows Only
No local installation with Windows Home if connected to the internet
Pro -> personal use -> Offline account -> limited experience

## Install Volatility
http://downloads.volatilityfoundation.org/releases/2.6/volatility_2.6_win64_standalone.zip

### Install python 2
https://www.python.org/downloads/release/python-2714/
to add to path " C:\Python27"
Delete C:\Users\Username\AppData\Local\Microsoft\WindowsApps\ from path

## Install DumpIt
https://qpdownload.com/DumpIt/
https://my.comae.com/login
https://my.comae.com/tools
I had to register for an account.

### Windows 7
https://developer.microsoft.com/en-us/microsoft-edge/tools/vms/
IE11 on Windows 7
Already a VM


volatility_2.6_win64_standalone.exe -f IEWINT7-20191121-181018.dmp imageinfo
First profile Win8SP0x64
It didn't work, Win7SP0x64 did work
I followed this for Windows 7 https://www.aldeid.com/wiki/Volatility/Retrieve-password
