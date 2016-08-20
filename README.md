# Hackintosh


## OS 10.11.5
Steps:

1. Install clover v3625
2. Install mac os from real mac using usb adaptor to link the hard drive
3. Replace the clover folder under /volume/efi/.../CLOVER with CLOVER under this repo
4. Put ssdt-batc.aml(from repo, combine two batteries into one) and ssdt.aml(in ~/Library/ssdtPRGen after run ssdbPRGen.sh-Beta/ssdtPRGen.sh, get power management)
   Then run patch.sh in PatchAppleBacklight_v2 folder from repo and put all the generated .kext in ./patched into /efi/../clover/kext/other

DSDT.aml: follow the guide https://github.com/shmilee/T450-Hackintosh

What has been done:

1. Clover config.plist
2. To fix brightness:
  1. We have to patch the AppleIntelBDWGraphicsFramebuffer binary file in /S/L/E/AppleIntelBDWGraphicsFramebuffer.kext/Contents/MacOS/.
     Use app:HexFiend, find 39CF763C and replace it with 39CFEB3C for 10.10.x, replace 4139c4763e with 4139c4eb3e for 10.11.x.
  2. Do not use fakeID 0x16160002
  3. Use PatchAppleMacklight_v2, run on destination laptop and get the native brightness kext and put in kext/other/
  4. dsdt.aml should patch brightness_fix for hassel
3. To fix audio: dsdt.aml
                 install Voo..HDA, google and download it
