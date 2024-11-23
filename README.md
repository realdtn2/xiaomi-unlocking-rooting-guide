Even though this is written for Xiaomi 14T, it should work for most Xiaomi and other android devices

Rooting:

Step 1: Unlock your bootloader (Refer to https://github.com/bkerler/mtkclient/issues/1253#issuecomment-2453485808), for more detail check out https://xiaomi.eu/community/threads/all-in-one-xiaomi-14-houji-unlock-bootloader-root-flash-twrp-flash-rom.71645/ (ONLY FOLLOW THE UNLOCK BOOTLOADER SECTION)

Step 2: Get the ROMs files of your current firmware (About phone -> OS Version) (I got my firmware from here: https://miuirom.org/)

Step 3: Download and extract the firmware (You can use 7-Zip)

Step 4: Go to the "images" folder of the extracted firmware

Step 5: Copy the "init_boot.img" into a new folder on your desktop, then rename the file to "init_boot_stock.img" (YOU MUST NOT DELETE THIS INCASE OF BRICK)

Step 6: Copy "init_boot_stock.img" to your phone

Step 7: Install Magisk Alpha (https://install.appcenter.ms/users/vvb2060/apps/magisk/distribution_groups/public)

Step 8: Open Magisk Alpha -> Press top "Install" button -> Select and Patch a File -> Choose the "init_boot_stock.img" file -> After that it should give you a file similar to "magisk_patched-28001_p5r8c.img" in the Download folder of your phone

Step 9: Move the "magisk_patched-28001_xxxxx.img" to the same folder as "init_boot_stock.img" on your computer

Step 10: Enable USB Debugging in Developer Options

Step 11: Plug your phone in -> Allow computer on your phone -> Open cmd -> Type 'adb reboot fastboot' and press enter

Step 12: Go back to the folder you put your patched init_boot file, hold shift and right click "magisk_patched-28001_xxxxx.img", press copy as path

Step 13: Type ' fastboot flash init_boot_a "D:\Xiaomi 14T\Root\magisk_alpha_patched-28001_p5r8c.img" (the path here is just an example you can paste the path by pressing right click in the cmd) ' and press enter

Step 14: Type ' fastboot flash init_boot_b "D:\Xiaomi 14T\Root\magisk_alpha_patched-28001_p5r8c.img" (the path here is just an example you can paste the path by pressing right click in the cmd) ' and press enter

Step 15: Type ' fastboot reboot ' and press enter

Step 16: You should now be rebooted to the system and rooted


Hiding root:

Step 1: Go to Magisk Alpha Settings -> Hide Magisk App (You can name it to anything you want, I will be using "Settings") -> Disable Zygisk (Zygisk Next Will be used instead as the built-in Zygisk is detected in banking apps like vietnamese banks: Techcombank; MB Bank; VCB Digibank; ...) -> Enfore Denylist Off

Step 2: In Configure DenyList, choose the app you wish to hide root (Make sure to click the app THEN click the checkbox)

Step 3: Install the following magisk modules in this order: Play Intergrity Fix (https://github.com/chiteroman/PlayIntegrityFix/releases) + Tricky Store (https://github.com/5ec1cff/TrickyStore/releases) + Zygisk Next (https://github.com/Dr-TSNG/ZygiskNext/releases) + Zygisk Assistant (https://github.com/snake-4/Zygisk-Assistant/releases) + LSPosed (https://github.com/JingMatrix/LSPosed/releases) + Shamiko (https://github.com/LSPosed/LSPosed.github.io/releases)

Step 4: Reboot

Step 5: Install the Hide My Applist LSPosed module (https://github.com/Dr-TSNG/Hide-My-Applist/releases)

Step 6: Tap on the LSPosed notification to open the manager, then enable the Hide My Applist modules

Step 7: Open Hide My Applist -> Template manage -> Create a blacklist template -> Put whatever name you want -> Click the 'Edit list" of "app invisible" -> Check the following app: Hide My Applist, Settings (Hidden Magisk), any LSPosed modules that you will install in the future

Step 8: Go back to the first screen -> Click App manage -> Select apps that are detecting root -> Enable Hide -> Work Mode Blacklist (Default) -> Click "Using 0 templates" -> Choose the template you named -> Press back button and you should see enabled under the apps name

Step 9: Reboot (You don't need to reboot everytime you add an app to the "App manage" or "Template manage")


Hiding bootloader status:

Step 1: Find the package name of the app you wish to hide bootloader status (You can find it in Hide My Applist -> App Manage -> It should be below the App Name (example:com.xxx.xxx) )

Step 2: Install Termux (https://github.com/termux/termux-app/releases/download/v0.118.1/termux-app_v0.118.1+github-debug_arm64-v8a.apk)

Step 3: Open termux -> Type "pkg i tsu -y" (without the quotes) and press enter

Step 4: After the command finished running, type "sudo nano /data/adb/tricky_store/target.txt" and press enter

Step 5: Press the arrow down icon until the cursor reach the bottom

Step 6: Type in the package name of the app in Step 1

Step 7: Press CTRL, then press S to save the file

Step 8: Press CTRL, then press X to stop editing

Step 9: You can now close termux (Reboot is not neccessary if you already rebooted)


Why you need to install the modules:

- Play Intergrity Fix: It's in the name

- Tricky Store: Hide unlocked bootlooader status

- Zygisk Next: Better for hiding root than built-in Zygisk

- Shamiko & Zygisk Assistant: Also helps hide root


Tested on Xiaomi 14T Global

Images:

![image](https://github.com/user-attachments/assets/9095c40c-f120-4358-b7fa-58d34f73e1f0)
![image](https://github.com/user-attachments/assets/856057ba-45a0-42de-8e9f-b8b4fa38d03d)
![image](https://github.com/user-attachments/assets/65b9ccd2-98df-43c0-b530-2bda994d203e)
![image](https://github.com/user-attachments/assets/32bed38b-407a-4f6c-b583-ae7ec3e6af9c)
![image](https://github.com/user-attachments/assets/c383aab4-385d-4540-b3e1-15694ac43bf7)
![image](https://github.com/user-attachments/assets/6cb09d52-a83b-4308-beab-364c1fc42baf)
![image](https://github.com/user-attachments/assets/a98f5023-4862-40d7-8e8f-09620cd2c4b3)
![image](https://github.com/user-attachments/assets/74596ec2-21f7-405d-85e0-0006c112499e)
![image](https://github.com/user-attachments/assets/210824b1-00a3-4c3f-a8fe-ed45364a1479)
![image](https://github.com/user-attachments/assets/d1fe51d7-650b-4f0c-8830-ff11adca6209)
![image](https://github.com/user-attachments/assets/83963301-a37f-493c-b3d3-57978bb1eadc)
![image](https://github.com/user-attachments/assets/dea9bc94-6948-4684-849f-db2b9689e90f)
![image](https://github.com/user-attachments/assets/b59abb74-5f40-497e-affa-17c814925120)
