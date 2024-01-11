# Converting Bootable USB To Storage USB

PowerShell/Command Prompt + DiskPart will be used to convert a boot USB drive back to a regular storage USB drive.

1. Insert the boot USB drive into your computer.

2. Open PowerShell or Command Prompt.
![Screenshot 2023-12-06 115231](https://github.com/johnnyh209/Converting-Bootable-USB-To-Storage-USB/assets/33064730/631844a7-c7fe-4429-9f98-adcc545659bc)

3. Type in `diskpart` and press enter. This should open up a window for the DiskPart utility.
![WindowsTerminal_dRyhtwneQp](https://github.com/johnnyh209/Converting-Bootable-USB-To-Storage-USB/assets/33064730/30472899-1bae-4631-81d4-ab4a478b14da)

4. In the DiskPart window, type in `list disk`. This will list all of the drives/disks connected to your computer. In my case, I have 3 disks: two 931 GB-sized disks, and one 57 GB disk.
![diskpart_1u8sXcBnMU](https://github.com/johnnyh209/Converting-Bootable-USB-To-Storage-USB/assets/33064730/71dd8521-b1ca-4941-9e2c-60add4083755)

5. Select the correct disk by typing in `select disk [disk number]`. In my case, I know that Disk 2 is the USB drive, so I entered in `select disk 2`. Make sure that you are selecting the correct disk.
![diskpart_OAF7WXoixd](https://github.com/johnnyh209/Converting-Bootable-USB-To-Storage-USB/assets/33064730/13702be8-05bf-4970-9d98-ab1402caffce)

6. Type in `clean` to clean the disk you have selected. **WARNING: DiskPart's `Clean` will permanently erase all of the data that's on the selected drive.**
![diskpart_rExNUAZxY2](https://github.com/johnnyh209/Converting-Bootable-USB-To-Storage-USB/assets/33064730/cf86c79d-2ca6-4a05-84b3-23f44816bf12)

7. Type in `create partition primary` to create a primary partition on the drive.
![diskpart_B7Q6n3dTza](https://github.com/johnnyh209/Converting-Bootable-USB-To-Storage-USB/assets/33064730/30e49237-aed0-4e18-b35e-92375d9d7dd2)

8. While your drive now has a parition, you currently cannot write any files to it because it does not have a file system on it yet. 
