# ASRock-Z690M-ITX-ax-hackintosh
OpenCore hackintosh of the motherboard ASRock Z690m-itx/ax

# Specs
**Case** MeshRoom D （2\*USB 3.0 5Gbps, 1\*USB 3.0 Type-C 10Gbps<br>
**MB** ASRock-Z690M-ITX/ax<br>
**CPU** Intel Core i5-12600K<br>
**RAM** Crucial Pro DDR4 3200MHz 32G\*2<br>
**GPU** MSI Gaming AMD Radeon RX 6600XT MECH 2X 8G OC<br>
**SSDs** Topmore SSD 2TB（M.2) + WDC SN570 + Micron M500(SATA 3)<br>
**WLAN / BT** BCM 94352z（Replace the AX Wireless inside）<br>
**Monitor**<br>
DELL U2723QE monitor, 3840*2160, connected to DP1 port at 2160P@30bit<br>
Other specs are minor, use what you can find.<br>

# Environment<br>
110V 60Hz，United States<br>

# Availability of features
**System ver: macOS Monterey 12.7.3**<br>
**OpenCore ver:0.9.6**<br>
**Using Windows 11 and macOS installed on separate disks. You need to move the ```Microsoft``` folder in Windows EFI partition to the OC EFI folder.**<br>
Wi-Fi 5, connection speed 867Mbps. Airdrop can only go from your iPhone/iPad to hackintosh. Hackintosh cannot AirDrop its files to other devices. **Replace with BCM94360NG to solve this problem, remember to delete two BCM related kexts.**<br>
**No Intel Wi-Fi driver!!! Do it yourself.**<br>
**Some USB ports may not work.** This MB really sucks, all 28 USB ports on one XHCI controller, macOS Monterey and later does not support so many USB ports on a single controller. In a nutshell, front panel tyep-C and USB 3.0 works perfectly, **all USB 2.0 pins will not work.**<br>
Fan speed cannot be obtained. This means in macOS you cannot monitor the fan speed, otherwise it returns 65535rpm. You cannot use MacsFanControl or something like that to manually control your fan speed.
**Newer versions of Final Cut Pro will stuck.** Use versions of Final Cut Pro released before your system version's release. Otherwise, enjoy getting stuck for seconds every cut.<br>

# Compatibility
CPU can be any 12/13/14 gen Intel Core processor. Avoid using ES CPUs or wierd MoDT modified CPUs, if any. ES CPUs will work but may require a bit extra work. MoDT modified CPUs will not work.<br>
GPU can be any supported hackintosh AMD GPU, in theory RX6950XT will be the highest performance, but need modification so the best I think you can use is RX6900XT.<br>
You can use other motherboard, do a bit modification by yourself. But you are here to copy my EFI, not do this type of deep modification.

# BIOS settings
### How to enter BIOS settings
Use wired or wireless keyboard with a receiver, F2 enter BIOS, F6 into advanced.<br>
### Turn off these options<br>
Fast Boot<br>
Secure Boot<br>
VT-d<br>
### Turn on these options<br>
VT-x<br>
Above 4G decoding<br>
Hyper- Threading<br>
USB XHCI Hand off<br>
SATA mode<br>
### Modify these options<br>
CSM --> Change all to UEFI<br>
### Do not change (i.e. If it is on leave it on, if it is off leave it off)<br>
Intel SGX<br>
CFG lock<br>

# Problems encountered
Using a wired mouse or keyboard (including wireless receiver) will cause a ```bluetoothd``` crash record in Monterey and later. But no harm done, everything is operating good.<br>
BCM94352z will be recognized as a third party dongle. Therefore the "Sharing" page in settings may occasionally crash.