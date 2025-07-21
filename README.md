
# Unlocking bootloader, rooting, hiding root, Play Integrity, and hiding unlocked bootloader status for Xiaomi devices (this guide should work for most of the newer Xiaomi devices with HyperOS/HyperOS 2.0)

---

## Unlocking the bootloader (HyperOS)

### Warning
- BACK UP ANY DATA YOU MAY HAVE ON YOUR PHONE; THIS WILL FACTORY RESET YOUR PHONE.

### Requirements
- Your Xiaomi account must be over 30 days old.
- Enable **Find device** in **Xiaomi Cloud** in the Settings app (this may not be necessary, but you should do it to be sure).

### Step 1: Enable OEM Unlocking
- In the Settings app, go to  **About phone**, and then tap the **OS version** 5 times.
- Enable **OEM Unlocking** from **Developer Options**.

### Step 2: Reinstall Xiaomi Community
- Uninstall Xiaomi Community, reboot, and then install the latest version of Xiaomi Community via the Play Store.

### Step 3: Change account's region
- Sign in to your Xiaomi account through the Xiaomi Community app.
- Go to the **Me** tab, scroll down and select **Set up**.
- Select **Change region** and choose **Global**.

### Step 4: Apply for unlocking
- At exactly 12:00 AM GMT+8, press "Apply for unlocking" (If you do this too late, you may encounter an "application quota limit reached" error, so ensure you act precisely at 12:00 AM GMT+8, you can use this [site](https://time.is/GMT+8) to check the time).
- It might display an "Account Error". If that happens, you'll need to retry after 10 days, just like I did.
<p>
   <img src="https://github.com/user-attachments/assets/6ff58a4f-1913-48ea-8950-1b9287600611" alt="Image 1" width="200" height="auto" style="margin-right: 10px;">
   <img src="https://github.com/user-attachments/assets/9176ad6b-c9d8-4e71-bcfa-f7ad6de28ae4" alt="Image 1" width="200" height="auto">
</p>

### Step 5: Add your account to Mi Unlock
- Turn off your Wi-Fi and ensure you have a working mobile data connection.
- In **Developer Options**, scroll down until you see **Mi Unlock status**, select it, and press **Add account and device**.

### Step 6: Download the Mi Unlock tool
- Download the latest version of the tool from [here](https://miuirom.org/updates/mi-flash-unlock).

### Step 7: Sign in to your Xiaomi account in the Mi Unlock tool
- After downloading the tool, extract it, navigate to the extracted folder, and open **miflash_unlock.exe**.
- It will prompt you to sign in.
- After signing in, agree to the disclaimer.

### Step 8: Download ADB and Fastboot tools
- Go to this [site](https://developer.android.com/tools/releases/platform-tools?hl=en) and select the one for Windows.
- Download it and extract it. You should now see a folder named `platform-tools`.
- Navigate to the extracted folder, click on the address bar, and replace everything in the address bar with **cmd**, and then press enter and a CMD window should show up.

### Step 9: Enable USB Debugging
- Enable **USB Debugging** from **Developer Options**.

## Step 10: Unlocking the bootloader
- Plug your phone in and press allow computer when prompted on the phone.
- In the CMD window that you opened in step 8, type `adb.exe reboot fastboot` and press enter.
- Your phone should reboot and show the text FASTBOOT.
- In the Mi Unlock app, it should say phone connected. Now press unlock, and then press unlock anyway.
- It might say couldn't unlock; you have to wait for the amount of hours that is displayed (During this waiting time, DO NOT log out of your Xiaomi account on the phone or the Xiaomi Community app).
- After waiting for the specified amount of hours, do the same unlocking process and this time your phone should be unlocked.

---

## Rooting

### Disclaimer: `init_boot` is for newer devices. If your device does not have `init_boot`, replace `init_boot` with `boot` instead.
### Tip: Disable auto-update in the update settings if you don't want to root again every time.

### Step 1: Obtain ROM Files
1. Navigate to **About phone -> OS Version** on your device.
2. Download the firmware (Fastboot ROM) from [miuirom.org](https://miuirom.org/) corresponding to your device and OS Version.

### Step 2: Extract Firmware
- Use tools like **7-Zip** to extract the firmware.

### Step 3: Locate the `images` Folder
- Navigate to the `images` folder within the extracted firmware files.

### Step 4: Backup `init_boot.img`
1. Copy `init_boot.img` to the `platform-tools` folder that you extracted in Step 8 of **unlocking the bootloader**.
2. Rename it to `init_boot_stock.img` (DO NOT DELETE THIS FILE IN CASE OF A BRICK).

### Step 5: Transfer to Phone
- Transfer the `init_boot_stock.img` file to your phone.

### Step 6: Install Magisk Alpha
- Download and install Magisk Alpha from [this link](https://install.appcenter.ms/users/vvb2060/apps/magisk/distribution_groups/public).
- If the site is down, please try [Magisk Alpha (28102)](https://github.com/realdtn2/xiaomi-unlocking-rooting-guide/raw/refs/heads/main/magisk_alpha-28102.apk)

### Step 7: Patch the `init_boot_stock.img`
1. Open the Magisk Alpha app.
2. Tap **Install** -> **Select and Patch a File**.
3. Choose `init_boot_stock.img`.
4. The patched file will appear as something like `magisk_patched-28001_p5r8c.img` in your phone's Download folder.

### Step 8: Transfer Patched File to PC
- Move the patched file (`magisk_patched-28001_xxxxx.img`) to the `platform-tools` folder on your computer.

### Step 9: Reboot to Fastboot
1. Connect your phone to the computer.
2. Navigate to the `platform-tools` folder, click on the address bar, and replace everything in the address bar with **cmd**, and then press enter and a CMD window should show up.
3. Run the following command in CMD:
   ```
   adb.exe reboot fastboot
   ```

### Step 10: Flash Patched `init_boot`
1. In the same CMD window, execute the following commands:
   ```
   fastboot.exe flash init_boot_a magisk_patched-28001_xxxxx.img (e.g., fastboot.exe flash init_boot_a magisk_patched-28001_p5r8c.img)
   fastboot.exe flash init_boot_b magisk_patched-28001_xxxxx.img (e.g., fastboot.exe flash init_boot_b magisk_patched-28001_p5r8c.img)
   fastboot.exe reboot
   ```
   For older devices without `init_boot` (DO NOT FOLLOW THESE COMMANDS IF YOUR DEVICE ALREADY HAVE `init_boot`):
   ```
   fastboot.exe flash boot_a magisk_patched-28001_xxxxx.img (e.g., fastboot.exe flash boot_a magisk_patched-28001_p5r8c.img)
   fastboot.exe flash boot_b magisk_patched-28001_xxxxx.img (e.g., fastboot.exe flash boot_b magisk_patched-28001_p5r8c.img)
   fastboot.exe reboot
   ```
   For older devices without `init_boot`, if there's an error, try running this command:
   ```
   fastboot.exe --disable-verity --disable-verification flash vbmeta vbmeta.img (vbmeta.img is from the firmware you downloaded)
   ```

Your device should be rebooted to the system and have root access.

---

## Hiding Root (You SHOULD be able to use this hiding root section with most Android devices like Xiaomi, Samsung, etc.)


### Step 1: Hide Magisk App
1. Open the Magisk Alpha app.
2. Go to **Settings** -> **Hide Magisk App** (You can name it anything, e.g., `Settings`).
3. Disable **Zygisk**.
4. Turn **Enforce Denylist** OFF.

### Step 2: Configure DenyList
1. Navigate to **Configure DenyList**.
2. Select the apps you want to hide root from (tap the app, and then tap on the checkbox).

### Step 3: Install Required Magisk Modules
Install the following modules in this order:
- [Zygisk Next](https://github.com/Dr-TSNG/ZygiskNext/releases)
- [Tricky Store](https://github.com/5ec1cff/TrickyStore/releases)
- [Zygisk Assistant](https://github.com/snake-4/Zygisk-Assistant/releases)
- [LSPosed](https://github.com/JingMatrix/LSPosed/releases)
- [Shamiko](https://github.com/LSPosed/LSPosed.github.io/releases)

### Step 4: Reboot

### Step 5: Install Hide My Applist
1. Install the [Hide My Applist module](https://github.com/Dr-TSNG/Hide-My-Applist/releases).
2. Enable it via LSPosed manager.

### Step 6: Configure "Template manage"
1. On the home screen of "Hide My Applist", go to **Template manage** and create a blacklist template.
2. Name it anything, and add the following to **Apps Invisible**:
   - Hide My Applist
   - Settings (Hidden Magisk App) (If you unhide the Magisk Alpha app, you have to add it back when you hide it again)
   - Any LSPosed modules you will install in the future

### Step 7: Configure "App Manage"
1. On the home screen of "Hide My Applist", go to **App Manage** and select the apps that are detecting root.
2. Select "Enable Hide" -> Set "Work Mode" to Blacklist (default option) -> Select "Using 0 templates" and choose the template you named.

---

## Play Integrity Fix (MAY 2025)

As of May 2025, Google has rolled out major changes to the Play Integrity API, follow these steps to fix it:
### Step 1: Install Required Magisk Modules
Make sure you already have the [Play Integrity Fix](https://github.com/chiteroman/PlayIntegrityFix/releases) and [Tricky Store](https://github.com/5ec1cff/TrickyStore/releases) modules installed in Step 3 of **Hiding Root**, then install the following modules:
- [PlayIntegrityFix](https://github.com/KOWX712/PlayIntegrityFix/releases) (download the newest **inject-s** version)
- [Tricky Store Addon](https://github.com/KOWX712/Tricky-Addon-Update-Target-List/releases)
- [Busybox](https://mmrl.dev/repository/grdoglgmr/busybox-ndk)
- [Yuri Keybox Manager](https://github.com/dpejoh/yurikey/releases)

### Step 2: Reboot

### Step 3: Configure PlayIntegrityFix
1. Open the Magisk Alpha app.
2. Go to **Modules**, click on the **Action** button of the **PlayIntegrityFix** module.
3. Click on the **Advanced** button, and make sure **Use preview fingerprint**, **Spoof Build**, **Spoof Provider**, **Spoof Props**, and **Spoof Signature** are toggled on.
4. Click on the **Fetch pif.json** button, and wait for it to be done

### Step 4: Configure Yuri Keybox Manager
1. Open the Magisk Alpha app.
2. Go to **Modules**, click on the **Action** button of the **Tricky Store** module, this will install **KsuWebUI** if you do not have **KsuWebUI** or **MMRL** installed.
3. Open the **KsuWebUI** app and click on **Yuri Keybox Manager**.
4. Go to the **Menu** tab
5. Click **Set Up Yuri Keybox**, **Set Up Security Patch**, **Set Up Verified Boothash**, **Set up Target.txt**, and **Force Stop & Clear Data Play Store**

### Step 5: Reboot

### Step 6: Check the Integrity
- Use this [app](https://play.google.com/store/apps/details?id=gr.nikolasspyr.integritycheck&hl=en)

### Note: Do not change keybox too frequently, or preferably, not at all. If you check too frequently, Google will get suspicious.
### Reminder: If you suddenly fail to pass Play Integrity, do Step 3 & 4 again.

<p>
   <img src="https://github.com/user-attachments/assets/af8dcfd8-8ffa-4694-b500-63b78e527316" alt="Image 1" width="200">
</p>

> <span style="opacity:0.6"> Some custom ROMS spoof old fingerprints (PIF's) by default, you'd need to disable that functionality if your rom has it built in, I can't help much for this part.</span>


---

## Hiding Bootloader Status

### Step 1: Install Required Magisk Modules
Make sure the [Tricky Store](https://github.com/5ec1cff/TrickyStore/releases) and [Tricky Store Addon](https://github.com/KOWX712/Tricky-Addon-Update-Target-List/releases) modules are installed.

### Step 2: Configure Tricky Store
1. Open the Magisk Alpha app.
2. Go to **Modules**, click on the **Action** button of the **Tricky Store** module, this will install **KsuWebUI** if you do not have **KsuWebUI** or **MMRL** installed.

### Step 3: Adding Apps
1. Open the **KsuWebUI** app and click on **Tricky Store**.
2. You can search for the apps you'd like to hide bootloader status from, then check the box for it.
3. Hit the blue **Save** button at the center bottom of the screen, scroll to top if you don't see the button.

---

## Tested and found to be working on the following devices (I'd appreciate it if you guys could report it back to me your device if in **Issues** if it works for you)
- Xiaomi 14T (Global) (HyperOS)
- Redmi K60 Ultra 5G (HyperOS/HyperOS 2.0)
- Xiaomi Mi 11 Ultra (HyperOS)

---

## Images
<p>
   <img src="https://github.com/user-attachments/assets/9095c40c-f120-4358-b7fa-58d34f73e1f0" alt="Image 1" width="200" style="margin-right: 150px;">
   <img src="https://github.com/user-attachments/assets/856057ba-45a0-42de-8e9f-b8b4fa38d03d" alt="Image 2" width="200" style="margin-right: 150px;">
   <img src="https://github.com/user-attachments/assets/65b9ccd2-98df-43c0-b530-2bda994d203e" alt="Image 3" width="200" style="margin-right: 150px;">
   <img src="https://github.com/user-attachments/assets/32bed38b-407a-4f6c-b583-ae7ec3e6af9c" alt="Image 4" width="200" style="margin-right: 150px;">
   <img src="https://github.com/user-attachments/assets/de201456-21d5-4882-bd3e-ceb6b39c56bf" alt="Image 5" width="200" style="margin-right: 150px;">
   <img src="https://github.com/user-attachments/assets/6cb09d52-a83b-4308-beab-364c1fc42baf" alt="Image 6" width="200" style="margin-right: 150px;">
   <img src="https://github.com/user-attachments/assets/a98f5023-4862-40d7-8e8f-09620cd2c4b3" alt="Image 7" width="200" style="margin-right: 150px;">
   <img src="https://github.com/user-attachments/assets/74596ec2-21f7-405d-85e0-0006c112499e" alt="Image 8" width="200" style="margin-right: 150px;">
   <img src="https://github.com/user-attachments/assets/210824b1-00a3-4c3f-a8fe-ed45364a1479" alt="Image 9" width="200" style="margin-right: 150px;">
   <img src="https://github.com/user-attachments/assets/d1fe51d7-650b-4f0c-8830-ff11adca6209" alt="Image 10" width="200" style="margin-right: 150px;">
   <img src="https://github.com/user-attachments/assets/83963301-a37f-493c-b3d3-57978bb1eadc" alt="Image 11" width="200" style="margin-right: 150px;">
   <img src="https://github.com/user-attachments/assets/4134ecbb-c89c-4e69-82ec-b00429ab0839" alt="Image 12" width="200" style="margin-right: 150px;">
   <img src="https://github.com/user-attachments/assets/b59abb74-5f40-497e-affa-17c814925120" alt="Image 13" width="200" style="margin-right: 150px;">
   <img src="https://github.com/user-attachments/assets/08372f3b-8e40-4293-9e3a-85095f02850d" alt="Image 13" width="200" style="margin-right: 150px;">
   <img src="https://github.com/user-attachments/assets/0935505c-bf30-438c-999f-2ff045da6aa9" alt="Image 13" width="200">
</p>
