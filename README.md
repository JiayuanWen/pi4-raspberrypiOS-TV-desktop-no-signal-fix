### Devices:
* Sony Bravia KDL-42EX440 LCD TV
* Raspberry Pi 4 Model B (2GB) 
    * OS: Raspberry Pi OS (Raspbian) 11 bullseye


### Problem:
When connecting Pi 4 to TV via Micro-HDMI to HDMI, the boot-loader and initial splash shows up. As soon as the desktop loads, the TV shows no signal. 

### Solution:
Raspberry Pi OS (Raspbian) 11 uses KMS driver by default, which is not compatable with this TV model. We need to switch to FKMS drivers.
1. Find a way to access your system file in Pi (either via SSH, use secondary PC monitor, or plug your Pi's SDcard to a working PC and access the partition where `/boot` is located)
2. Edit `config.txt` in your `/boot` system folder as a super user. Ex: `$ sudo nano /boot/config.txt`
3. Find the line `dtoverlay=vc4-kms-v3d`, change it to `dtoverlay=vc4-fkms-v3d`. Uncomment if it is commented out, add if line doesn't exist.
