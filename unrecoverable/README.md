# How To Make Data Unrecoverable
## Mechanical HDD (Hard Disk Drive)
## Live USB Debian-based distribution
```bash
# Note: You must run shred with sudo privileges to target raw devices
sudo shred -n 5 -vz /dev/sdx
```
* Tip: Run `lsblk` first to correctly identify `/dev/sdx` and avoid erasing the wrong drive.

## SSD (Solid State Drive)
## Secure erase single file
To securely delete a specific file, you must first delete it normally (`rm` or drag to trash), then immediately run `fstrim` on the directory's mount point (not the file path itself).
```bash
# 1. Delete the file
rm /path/to/file.txt
# 2. Force TRIM on the drive partition (e.g., the root filesystem '/')
sudo fstrim -v /
```
## NVMe SSD
```bash
# 1. List all connected NVMe devices
sudo nvme list
# 2. Hardware-level block erase (Overwrites all NAND cells)
sudo nvme sanitize /dev/nvme0n1 -a start-block-erase
# 3. Cryptographic erase (Destroys internal encryption key instantly)
sudo nvme sanitize /dev/nvme0n1 -a start-crypto-erase
```
## SATA SSD
```bash
# 1. Check if the drive status is "not frozen"
sudo hdparm -I /dev/sdX
# Note: If "frozen", put the computer to sleep (suspend) and wake it up to unlock it.
# 2. Set a temporary required master password
sudo hdparm --user-master u --security-set-pass TempPassword /dev/sdX
# 3. Execute the internal hardware factory reset
sudo hdparm --user-master u --security-erase TempPassword /dev/sdX
```
## UEFI Motherboard Menu
1. Restart the computer and enter motherboard BIOS/UEFI menu (tap `F2`, `F12`, `F8`, or `Del` at startup).
2. Navigate to the **Tools**, **Security**, or **Storage** tabs.
3. Look for a built-in utility named "NVMe Sanitize", "Secure Erase", or "SSD Wipe".
4. Select the target SSD and run it directly from the motherboard. (Best method if erasing the host drive you normally boot into).

# End Result
Now all private and sensative data (images, pictures, videos, etc) from the computer is **100% unrecoverable**. One can now install a new OS from live USB boot or safely dispose at e-waste location.
