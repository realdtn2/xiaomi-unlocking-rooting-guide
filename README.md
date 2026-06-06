# Bootloader Unlock / Root / Hide Root/ Play Integrity/ Spoof Bootloader Status as Locked (Key Attestation) for Xiaomi devices (HyperOS/HyperOS 2.0/HyperOS 3.0) (Global) [2026] 

# Bootloader Unlock

## Warning
- **BACK UP ANY DATA YOU MAY HAVE ON YOUR PHONE**
- **ALL OF YOUR DATA WILL BE WIPED**

## Requirements
- Your **Xiaomi account** must be over **30 days old**
- Enable **Find device** in **Xiaomi Cloud** in **Settings** (might not be necessary, but enable for certainty)

### Step 1: Enable OEM Unlocking
- In **Settings**, press **About phone** and tap **OS version** 5 times to unlock **Developer Options**
- In **Developer Options**, enable **OEM Unlocking**

### Step 2: Reinstall Xiaomi Community
- Uninstall **Xiaomi Community** and reboot
- Install the **latest version** of **Xiaomi Community** on the **Play Store**

### Step 3: Account Region
- Sign in with your **Xiaomi account** in **Xiaomi Community**
- In the **Me** tab, find **Set up** and press it
- Press **Change region** and choose **Global**

### Step 4: Apply for unlocking
- Press "Apply for unlocking" at exactly **12:00 AM GMT+8** (pressing it too late will cause the **"application quota limit reached"** error. Use this [website](https://time.is/GMT+8) to check the time)
- **"Account Error"** might show up. If that happens, retry after 10 days
- **Tip:** If it keeps failing, try another method using this[ Python automation script](https://xdaforums.com/t/how-to-unlock-bootloader-on-xiaomi-hyperos-all-devices-except-cn.4654009/#post-89311595)

### Step 5: Bootloader Unlock Preparation
- Logout of your **Xiaomi account** in **Settings**
- Reboot
- Login again with your **Xiaomi account** in **Settings**

### Step 6: Add account to Mi Unlock
- Turn off **Wi-Fi** and make sure a **working mobile data connection** is available
- In **Developer Options**, find **Mi Unlock status** and press it
- Press **Add account and device**

### Step 7: Mi Unlock tool
- Download the **latest version** of it from [here](https://miuirom.org/updates/mi-flash-unlock)

### Step 8: Sign in to your Xiaomi account
- After download, extract and navigate to its folder
- Open **miflash_unlock.exe**, you will be prompted to sign in
- After signing in, **agree to the disclaimer**

### Step 9: ADB and Fastboot
- Enter this [site](https://developer.android.com/tools/releases/platform-tools?hl=en) and select the one for **Windows**
- After download, extract and navigate to its folder
- Click on the **address bar** of the folder and replace everything with **cmd**
- Press enter and a **CMD window** should pop up

### Step 10: USB Debugging
- In **Developer Options**, enable **USB Debugging**

### Step 11: Bootloader Unlock
- Plug in your phone and press **allow computer** when prompted on the phone
- In the **CMD window** opened in **step 9**, type `adb.exe reboot fastboot` and press enter
- Your phone should reboot and display **FASTBOOT**
- In the Mi Unlock app, it should display **phone connected**
- Press **unlock** and then press **unlock anyway**
- It might say **couldn't unlock**; wait for the amount of time displayed (during this time, **DO NOT** log out of your **Xiaomi account** on the phone or in **Xiaomi Community**)
- When **enough time** has passed, repeat **this step** and your phone should be unlocked

---

# Root

## Disclaimer: `init_boot` is for newer devices. Older devices do not have `init_boot`, so only use `boot` on those

## Tip: Disable auto-update in the Settings to prevent losing root

> <details>
> <summary><b>KernelSU (recommended — install to check if your phone is supported) (Android 12+) </b></summary>
>
> ### Step 1: Obtain ROM Files
> 1. Navigate to **About phone** on your device
> 2. Download the firmware **(Fastboot ROM)** from [miuirom.org](https://miuirom.org/) that matches **your device** and **OS version**
>
> ### Step 2: Extract Firmware
> - After download, extract and navigate to its folder
>
> ### Step 3: Locate the `images` Folder
> - Find the `images` folder and enter it
>
> ### Step 4: Backup `init_boot.img`
> 1. In the folder, copy `init_boot.img` to the `platform-tools` folder in **Step 9 of unlocking the bootloader**
> 2. Rename the copied file to `init_boot_stock.img` (DO NOT DELETE IN CASE OF A BRICK)
>
> ### Step 5: Transfer to Phone
> - Transfer the `init_boot_stock.img` file to your phone
>
> ### Step 6: Install KernelSU
> - Download and install the **latest APK** from their **releases**    
> https://github.com/tiann/KernelSU/releases
>
> ### Step 7: Check KernelSU compatibility
> 1. Open **KernelSU**
> 2. If the app shows **Not installed**, then your device is **officially supported** by **KernelSU**      
>    If the app shows **Unsupported**, it means that you should **compile the kernel yourself**, **KernelSU** won't and never provide files for you to flash
>
> ### Step 8: Patch the `init_boot_stock.img`
> 1. Open **KernelSU**
> 2. Click on **Not installed - Tap to install** -> **Select a file**.
> 3. Choose `init_boot_stock.img`
> 4. Click on **Next** and choose the option with **This device KMI**
> 5. Press **Confirm**
> 6. The **patched file** should be something like `kernelsu_patched_20260605_045957.img` in the **Download** folder of your phone
>
> ### Step 9: Transfer Patched File to PC
> - Move the **patched file** (`kernelsu_patched_20260605_045957.img`) to `platform-tools`
>
> ### Step 10: Reboot to Fastboot
> 1. Plug in your phone
> 2. Navigate to `platform-tools`, click on the **address bar** of the folder and replace everything with **cmd**
> 3. Press enter and a **CMD window** should pop up
> 4. Run the following command in CMD:
>    ```
>    adb.exe reboot fastboot
>    ```
>
> ### Step 11: Flash Patched `init_boot`
> 1. In the same CMD window, execute the following commands using it as an example:
>    ```
>    fastboot.exe flash init_boot_a kernelsu_patched_20260605_045957.img
>    fastboot.exe flash init_boot_b kernelsu_patched_20260605_045957.img
>    fastboot.exe reboot
>    ```
>
> 2. Your device should reboot into the system and be rooted
>
> </details>

> <details>
> <summary><b>Magisk Alpha</b></summary>
>
> ### Step 1: Obtain ROM Files
> 1. Navigate to **About phone** on your device
> 2. Download the firmware **(Fastboot ROM)** from [miuirom.org](https://miuirom.org/) that matches **your device** and **OS version**
>
> ### Step 2: Extract Firmware
> - After download, extract and navigate to its folder
>
> ### Step 3: Locate the `images` Folder
> - Find the `images` folder and enter it
>
> ### Step 4: Backup `init_boot.img`
> 1. In the folder, copy `init_boot.img` to the `platform-tools` folder in **Step 9 of unlocking the bootloader**.
> 2. Rename the copied file to `init_boot_stock.img` (DO NOT DELETE IN CASE OF A BRICK)
>
> ### Step 5: Transfer to Phone
> - Transfer the `init_boot_stock.img` file to your phone
>
> ### Step 6: Install Magisk Alpha
> - Download and install the **latest version** of Magisk Alpha from their [Telegram Channel](https://t.me/magiskalpha)
>
> ### Step 7: Patch the `init_boot_stock.img`
> 1. Open **Magisk Alpha**
> 2. Tap **Install** -> **Select and Patch a File**
> 3. Choose `init_boot_stock.img`
> 4. The **patched file** should be something like `magisk_patched-XXXXX_xxxxx.img` in the **Download** folder of your phone
>
> ### Step 8: Transfer Patched File to PC
> - Move the **patched file** (`magisk_patched-XXXXX_xxxxx.img`) to `platform-tools`
>
> ### Step 9: Reboot to Fastboot
> 1. Plug in your phone
> 2. Navigate to `platform-tools`, click on the **address bar** of the folder and replace everything with **cmd**
> 3. Press enter and a **CMD window** should pop up
> 4. Run the following command in CMD
>    ```
>    adb.exe reboot fastboot
>    ```
>
> ### Step 10: Flash Patched `init_boot`
> 1. In the same CMD window, execute the following commands
>    ```
>    fastboot.exe flash init_boot_a magisk_patched-28001_xxxxx.img (e.g., fastboot.exe flash init_boot_a magisk_patched-28001_p5r8c.img)
>    fastboot.exe flash init_boot_b magisk_patched-28001_xxxxx.img (e.g., fastboot.exe flash init_boot_b magisk_patched-28001_p5r8c.img)
>    fastboot.exe reboot
>    ```
>    **Only** for **OLD DEVICES** without `init_boot` ***(DO NOT FOLLOW IF YOUR DEVICE HAVE `init_boot`)***
>    ```
>    fastboot.exe flash boot_a magisk_patched-28001_xxxxx.img (e.g., fastboot.exe flash boot_a magisk_patched-28001_p5r8c.img)
>    fastboot.exe flash boot_b magisk_patched-28001_xxxxx.img (e.g., fastboot.exe flash boot_b magisk_patched-28001_p5r8c.img)
>    fastboot.exe reboot
>    ```
>    **Only** for **OLD DEVICES** without `init_boot`, if there's an **error**, try running this command ***(DO NOT FOLLOW IF YOUR DEVICE HAVE `init_boot`)***
>    ```
>    fastboot.exe --disable-verity --disable-verification flash vbmeta vbmeta.img (vbmeta.img is from the firmware you downloaded)
>    ```
>
> 2. Your device should reboot into the system and be rooted
>
> </details>

---

# Hide Root/ Play Integrity Fix/ Spoof Bootloader Status as Locked (Key Attestation)

## Requirements

> <details>
> <summary><b>KernelSU</b></summary>
>
> ### Step 1: Install Required Magisk/ KernelSU Modules
> Install the **latest release version** of the following modules in this order:
> - Hybrid Mount (reboot your phone)  
>   https://github.com/Hybrid-Mount/meta-hybrid_mount/releases
> - Zygisk Next (reboot your phone)  
>   https://github.com/Dr-TSNG/ZygiskNext/releases
> - TEESimulator-RS (Way Better Alternative to Tricky Store)  
>   https://github.com/Enginex0/TEESimulator-RS/releases
> - Tricky Addon Enhanced (auto-fetch keyboxes)  
>   https://github.com/Enginex0/tricky-addon-enhanced/releases (press Vol+ when asked)
> - Vector (LSPosed fork)  
>   https://github.com/JingMatrix/Vector/releases
> - PlayIntegrityFix (inject-s)  
>   https://github.com/KOWX712/PlayIntegrityFix/releases
> - Shamiko  
>   https://github.com/LSPosed/LSPosed.github.io/releases
>
> ### Step 2: Reboot
>
> </details>

> <details>
> <summary><b>Magisk Alpha</b></summary>
>
> ### Step 1: Install Required Magisk Modules
> Install the **release version** of the following modules in this order:
> - Zygisk Next (reboot your phone)  
>   https://github.com/Dr-TSNG/ZygiskNext/releases
> - TEESimulator-RS (Way Better Alternative to Tricky Store)  
>   https://github.com/Enginex0/TEESimulator-RS/releases
> - Tricky Addon Enhanced (auto-fetch keyboxes)  
>   https://github.com/Enginex0/tricky-addon-enhanced/releases (press Vol+ when asked)
> - Vector (LSPosed fork)  
>   https://github.com/JingMatrix/Vector/releases
> - PlayIntegrityFix (inject-s)  
>   https://github.com/KOWX712/PlayIntegrityFix/releases
> - Shamiko  
>   https://github.com/LSPosed/LSPosed.github.io/releases
>
> ### Step 2: Reboot
>
> </details>

## Hide Root (should be compatible with most Android devices like Xiaomi, Samsung, etc.)

> <details>
> <summary><b>KernelSU</b></summary>
>
> ### Step 1: Install KsuWebUI
> - Download and install the latest version of KsuWebUI from  
>   https://github.com/5ec1cff/KsuWebUIStandalone/releases
>
> ### Step 2: Set up KernelSU
> 1. Open **KernelSU**
> 2. Go to **Settings** → Turn off **Kernel unmount**
>
> ### Step 3: Configure Zygisk Next
> 1. Open **KsuWebUI**
> 2. Click on the **Zygisk Next** module
> 3. Set **Denylist Policy** to **Unmount Only**
> 4. Turn on **Use anonymous memory**
>
> ### Step 4: Install Hide My Applist
> - Install Open Source HMA-OSS  
>   https://github.com/frknkrc44/HMA-OSS/releases
> - Enable it in the **LSPosed Manager** notification
>
> ### Step 5: Configure "Manage templates"
> 1. Open **HMA-OSS**
> 2. Go to **Manage templates**
> 3. Create a **blacklist template**
> 4. Name it anything
> 5. Edit list of **0 apps invisible**, add:
>    - HMA-OSS  
>    - KernelSU  
>    - All LSPosed modules installed
> 6. If new LSPosed modules are installed later, update this template again
>
> ### Step 6: Configure "Manage apps"
> 1. Open **HMA-OSS**
> 2. Go to **Manage apps**
> 3. Select the app(s) detecting root
> 4. Turn on **Enable hide**
> 5. Press **Template config**
> 6. Make sure **Work mode** is **Blacklist**
> 7. Press **Using 0 templates** and select your **blacklist template**
> 8. Confirm
>
> ### Step 7: Make sure Shamiko is toggled ON
>
> </details>

> <details>
> <summary><b>Magisk Alpha</b></summary>
>
> ### Step 1: Install KsuWebUI
> - Download and install the latest version of KsuWebUI from  
>   https://github.com/5ec1cff/KsuWebUIStandalone/releases
>
> ### Step 2: Hide Magisk App
> 1. Open **Magisk Alpha**
> 2. Go to **Settings** → **Hide Magisk App** (you can name it anything, e.g., `Settings`)
> 3. Disable **Zygisk**
> 4. Turn **Enforce Denylist** OFF
>
> ### Step 3: Configure DenyList
> 1. Navigate to **Configure DenyList**
> 2. Select the app(s) you want to **hide root** from (tap app first, then checkbox)
>
> ### Step 4: Configure Zygisk Next
> 1. Open **KsuWebUI**
> 2. Click on **Zygisk Next** module
> 3. Set **Denylist Policy** to **Enforced**
> 4. Turn on **Use anonymous memory**
>
> ### Step 5: Install Hide My Applist
> - Install Open Source HMA-OSS  
>   https://github.com/frknkrc44/HMA-OSS/releases
> - Enable it in the **LSPosed Manager** notification
>
> ### Step 6: Configure "Manage templates"
> 1. Open **HMA-OSS**
> 2. Go to **Manage templates**
> 3. Create a **blacklist template**
> 4. Name it anything
> 5. Edit list of **0 apps invisible**, add:
>    - HMA-OSS  
>    - Settings (hidden Magisk app or renamed one)  
>    - All LSPosed modules installed
> 6. If new modules are installed later, update this template again
>
> ### Step 7: Configure "Manage apps"
> 1. Open **HMA-OSS**
> 2. Go to **Manage apps**
> 3. Select the app(s) detecting root
> 4. Turn on **Enable hide**
> 5. Press **Template config**
> 6. Make sure **Work mode** is **Blacklist**
> 7. Press **Using 0 templates** and select your **blacklist template**
> 8. Confirm
>
> ### Step 8: Make sure Shamiko is toggled ON
>
> </details>

---

## Play Integrity Fix

### Step 1: Configure PlayIntegrityFix
1. Open the KsuWebUI app.
2. Click on the **Play Integrity Fix [INJECT]** module.
3. Make sure **Spoof Build** and **Spoof Build (Play Store)** is enabled
4. Click on **Fetch** and choose **GitHub** to get the **latest one**

### Step 2: Check the Integrity
- Use this [app](https://play.google.com/store/apps/details?id=gr.nikolasspyr.integritycheck&hl=en) to check it

### Note: If you suddenly fail to pass Play Integrity, do Step 1 again

<p>
   <img src="https://github.com/user-attachments/assets/af8dcfd8-8ffa-4694-b500-63b78e527316" alt="Image 1" width="200">
</p>

> <span style="opacity:0.6"> Some old custom ROMS spoof old fingerprints (PIF's) by default, you'd need to disable that functionality if your ROM has it built in, I can't help much for this part</span>


---

## Spoof Bootloader Status as Locked (Key Attestation)

### Step 1: Keybox Automation
1. Open **KsuWebUI**
2. Click on the **TEESimulator-RS** module
3. Click on the **3 dots** on the top right corner
4. Press **Keybox Automation**
5. You can set **Fetch Interval** to your liking or just leave it as it is
6. Find **Manual Actions** and click on **Fetch Key**

### Step 2: Select your app(s)
Search for the app(s) you want to **spoof bootloader status as locked**, then click on the checkbox for it

---

## Tested/ Working on the following devices (I'd appreciate it if you could report your device back to me in **Issues** if it works)
- Xiaomi 14T (HyperOS)
- Xiaomi Redmi K60 Ultra 5G (HyperOS/HyperOS 2.0)
- Xiaomi Mi 11 Ultra (HyperOS)
- Xiaomi 12 (Lineage OS 22.2)
- Xiaomi 13 Ultra (HyperOS 2.0)
- Xiaomi Redmi Note 15 5G (HyperOS 2.0)
- Poco F8 Pro (HyperOS 3.0)

---

## Images
<p>
   <img src="https://github.com/user-attachments/assets/6cb09d52-a83b-4308-beab-364c1fc42baf" alt="Image 1" width="200" style="margin-right: 150px;">
   <img src="https://github.com/user-attachments/assets/4134ecbb-c89c-4e69-82ec-b00429ab0839" alt="Image 2" width="200" style="margin-right: 150px;">
   <img src="https://github.com/user-attachments/assets/cf09561f-9642-4c08-8260-b8f2c70869e5" alt="Image 3" width="200" style="margin-right: 150px;">
   <img src="https://github.com/user-attachments/assets/0dffcdaa-2921-4e10-aa1b-40b2f2f9427e" alt="Image 4" width="200">
</p>
