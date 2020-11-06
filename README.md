# VBoxCloak

A PowerShell script that attempts to help malware analysts hide their Windows VirtualBox Windows VM's from malware that may be trying to evade analysis. Guaranteed to bring down your pafish ratings by at least a few points ;)

The script accomplishes this by doing the following:

- Renames several registry keys that malware typically uses for VM detection.
- Kills VirtualBox processes (VBoxService and VBoxTray).
- Deletes VirtualBox driver files (this will not crash VirtualBox, since these drivers are loaded into memory anyway!).
- Deletes or renames VirtualBox supporting files in System32 directory.

Tested on Windows 7 VM - probably works on Windows 10 and XP as well.

Spot any bugs? Let me know!

# Usage

1. Simply run VBoxCloak.ps1 as Administrator on your Windows VirtualBox VM.
2. Detonate your malware. Profit.
3. When done, reset your VM to clean state.

Usage examples:

Make registry changes, remove VBox files, and kill VBox processes:
  
  - "VBoxCloak.ps1 -all"
  
Just make registry modificaitons:
  
  - "VBoxCloak.ps1 -reg"
  
Just remove VBox files:
  
  - "VBoxCloak.ps1 -files"
  
Just kill VBox processes:
  
  - "VBoxCloak.ps1 -procs"

# Warnings & Disclaimers

- This code is in Beta. I know I cuould have coded it better, but sometimes quick and dirty is best.
- Use at your own risk! Use only in a VM, and NOT on your host.
- Ensure to make a snapshot of your VM before running this.-
- Using the "files" and/or "procs" command line arguments will likely result in slightly less VM performance. This is because this script removes several files that are required for supporting functions such as graphics, keyboard input, etc. Just revert VM to clean state if this messes anything up.

