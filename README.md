# Converting Bootable USB To Storage USB

PowerShell/Command Prompt + DiskPart will be used to convert a boot USB drive back to a regular storage USB drive.

1. Insert the boot USB drive into your computer.

2. Open PowerShell or Command Prompt.
<img src="https://github.com/johnnyh209/Converting-Bootable-USB-To-Storage-USB/assets/33064730/631844a7-c7fe-4429-9f98-adcc545659bc" Width="700" />

3. Type in `diskpart` and press enter. This should open up a window for the DiskPart utility.
<img src="https://github.com/johnnyh209/Converting-Bootable-USB-To-Storage-USB/assets/33064730/30472899-1bae-4631-81d4-ab4a478b14da" Width="700" />

4. In the DiskPart window, type in `list disk`. This will list all of the drives/disks connected to your computer. In my case, I have 3 disks: two 931 GB-sized disks, and one 57 GB disk.
<img src="https://github.com/johnnyh209/Converting-Bootable-USB-To-Storage-USB/assets/33064730/71dd8521-b1ca-4941-9e2c-60add4083755" Width="700" />

5. Select the correct disk by typing in `select disk [disk number]`. In my case, I know that Disk 2 is the USB drive, so I entered in `select disk 2`. Make sure that you are selecting the correct disk.
<img src="https://github.com/johnnyh209/Converting-Bootable-USB-To-Storage-USB/assets/33064730/13702be8-05bf-4970-9d98-ab1402caffce" Width="700" />

6. Type in `clean` to clean the disk you have selected. **WARNING: DiskPart's `Clean` will permanently erase all of the data that's on the selected drive.**
<img src="https://github.com/johnnyh209/Converting-Bootable-USB-To-Storage-USB/assets/33064730/cf86c79d-2ca6-4a05-84b3-23f44816bf12" Width="700" />

7. Type in `create partition primary` to create a primary partition on the drive.
<img src="https://github.com/johnnyh209/Converting-Bootable-USB-To-Storage-USB/assets/33064730/30e49237-aed0-4e18-b35e-92375d9d7dd2" Width="700" />

8. While your drive now has a partition, you currently cannot write any files to it because it does not have a file system on it yet. The file system is how your operating system stores and manages files. FAT, or File Allocation Table, is one type of file system that you would see on flash drives. Within the FAT category are FAT32 and exFAT. FA32 supports volume sizes up to 2TB, and a maximum file size of 4GB. FAT32 is older than exFAT, which supports file sizes that are larger than 4 GB. For my case, I will be going with exFAT. To write a file system onto the drive, use the `Format` command like so: `Format fs=exFAT quick`. `Format` is the name of the command, `fs=` declares the file system type, and `quick` performs a quick format.
<img src="https://github.com/johnnyh209/Converting-Bootable-USB-To-Storage-USB/assets/33064730/d8f6d902-9141-4345-9698-fbff15ac37dc" Width="700" />

9. Now that we have a file system on the drive, the last thing to do is to assign it a drive letter. We do so by typing in `assign`.
<img src="https://github.com/johnnyh209/Converting-Bootable-USB-To-Storage-USB/assets/33064730/de4244f6-8089-4e05-8607-806c45caceb1" Width="700" />

On Windows, if you open `File Explorer` and click on `This PC`, you should see the USB drive listed.

