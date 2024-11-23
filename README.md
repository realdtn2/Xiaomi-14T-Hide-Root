
# Rooting and Hiding Root for Xiaomi 14T (Global), should work for most Android devices

This guide details the steps to root your device and hide the root status, applicable to Xiaomi 14T (Global) and most Android devices.

## Unlocking the boootloader

### Warning
- BACK UP ANY DATA YOU MAY HAVE ON YOUR PHONE, THIS WILL FACTORY RESET YOUR PHONE..

### Requirements
- Account must be over 30 days old.
- Enable **Find device** in **Xiaomi Cloud** in the Settings app (Not sure if this is necessary).

### Step 1: Enable OEM Unlocking
- In the Settings app, go to  **About phone**, then tap the **OS version** 5 times.
- Enable **OEM Unlocking** from **Developer Options**.

### Step 2: Reinstall Xiaomi Community
- Uninstall Xiaomi Community, reboot, then reinstall via the Play Store.

### Step 3: Change account's region
- Sign in into your Xiaomi account through the Xiaomi Community app.
- Go to the **Me** tab, scroll down and select **Set up**.
- Select **Change region** and choose **Global**

### Step 4: Apply for unlocking
- Exactly at 12:00 AM GMT+8, press "Apply for unlocking" (If you do this too late, you may encounter an "application quota limit reached" error, so ensure you act precisely at 12:00 AM GMT+8).
- It might display an "Account Error". If that happens, you'll need to retry after 10 days, just like I did.
![image](https://github.com/user-attachments/assets/6ff58a4f-1913-48ea-8950-1b9287600611)
![image](https://github.com/user-attachments/assets/9176ad6b-c9d8-4e71-bcfa-f7ad6de28ae4)

### Step 5: Add your account to Mi Unlock
- Turn off your wifi and make sure you have a working mobile data connection.
- In **Developer Options**, scroll down until you see **Mi Unlock status**, select it and press **Add account and device**.

### Step 6: Download the Mi Unlock tool
- Download the tool from [here](https://server11.dosya.co/cgi-bin/azcl9.cgi/grjkptvs7hgquz5jk62agwrwgl5ot3kmjmlv7podvi/miflash_unlock_en_7.6.727.43.zip).

### Step 7: Sign in your Xiaomi's account in the Mi Unlock tool
- After you downloaded the extracted the tool, open **miflash_unlock.exe**.
- It will prompt you to sign in.
- After signing in, agree to the disclaimer.

### Step 8: Download ADB and Fastboot tools
- Go to this [site](https://developer.android.com/tools/releases/platform-tools?hl=en) and select the one for Windows.
- Download it and extract it, you should have a `platform-tools` folder.
- Navigate to the extracted folder, click on the address bar, and replace everything in the address bar with **cmd**, then press enter and a CMD window should show up.

### Step 9: Enable USB Debugging
- Enable **USB Debugging** from **Developer Options**.

## Step 10: Unlocking the bootloader
- Plug your phone in, allow computer when prompted on the phone
- In the CMD window that you opened in step 7, type "adb reboot fastboot".
- Your phone should reboot and show the orange text FASTBOOT.
- In the Mi Unlock app, it should says phone connected, now press unlock, after that press unlock anyway.
- It should says couldn't unlock and you have to wait for the amount of hours that is displayed.
- After waiting for the specificed amount of hours, do the same unlocking process and this time your phone should be unlocked.

## Rooting

### Step 1: Obtain ROM Files
1. Navigate to **About phone -> OS Version** on your device.
2. Download the firmware from [miuirom.org](https://miuirom.org/) based on your device and OS Version.

### Step 2: Extract Firmware
- Use tools like **7-Zip** to extract the firmware.

### Step 3: Locate the `images` Folder
- Navigate to the `images` folder within the extracted firmware files.

### Step 4: Backup `init_boot.img`
1. Copy `init_boot.img` to the `platform-tools` that you extracted on step 8 of **unlocking the bootloader**.
2. Rename it to `init_boot_stock.img` (DO NOT DELETE THIS FILE IN CASE OF A BRICK).

### Step 5: Transfer to Phone
- Transfer `init_boot_stock.img` to your phone.

### Step 6: Install Magisk Alpha
- Download and install Magisk Alpha from [this link](https://install.appcenter.ms/users/vvb2060/apps/magisk/distribution_groups/public).

### Step 7: Patch the `init_boot_stock.img`
1. Open Magisk Alpha.
2. Tap **Install** -> **Select and Patch a File**.
3. Choose `init_boot_stock.img`.
4. The patched file will appear as something like `magisk_patched-28001_p5r8c.img` in your phone's Download folder.

### Step 8: Transfer Patched File to PC
- Move the patched file (`magisk_patched-28001_xxxxx.img`) to the `platform-tools` on your computer.

### Step 9: Reboot to Fastboot
1. Connect your phone to the computer.
2. Navigate to the `platform-tools` folder, click on the address bar, and replace everything in the address bar with **cmd**, then press enter and a CMD window should show up.
3. Run the following command in CMD:
   ```
   adb.exe reboot fastboot
   ```

### Step 10: Flash Patched `init_boot`
1. On the same CMD window, execute the following commands:
   ```
   fastboot.exe flash init_boot_a magisk_patched-28001_xxxxx.img (e.g.: fastboot.exe flash init_boot_a magisk_alpha_patched-28001_p5r8c.img)
   fastboot.exe flash init_boot_b magisk_patched-28001_xxxxx.img (e.g.: fastboot.exe flash init_boot_b magisk_alpha_patched-28001_p5r8c.img)
   fastboot.exe reboot
   ```

Your device should be rebooted to the system and have root access.

---

## Hiding Root

### Step 1: Hide Magisk App
1. Open Magisk Alpha.
2. Go to **Settings** -> **Hide Magisk App** (You can name it anything, e.g., to `Settings`).
3. Disable **Zygisk**.
4. Turn **Enforce Denylist** OFF.

### Step 2: Configure DenyList
1. Navigate to **Configure DenyList**.
2. Select the apps you wish to hide root from (Click the app, then check the checkbox).

### Step 3: Install Required Magisk Modules
Install the following modules in this order:
- [Zygisk Next](https://github.com/Dr-TSNG/ZygiskNext/releases)
- [Play Integrity Fix](https://github.com/chiteroman/PlayIntegrityFix/releases)
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
2. Name it anything and add the following to **Apps Invisible**:
   - Hide My Applist
   - Settings (Hidden Magisk App)
   - Any LSPosed modules you will install in the future.

### Step 7: Configure "App Manage"
1. On the home screen of "Hide My Applist", go to **App Manage** and select apps detecting root.
2. Select "Enable Hide" -> Set "Work Mode" to Blacklist (default option) -> Select "Using 0 templates" and choose the template you named.

---

## Hiding Bootloader Status

### Step 1: Identify Package Name
1. Use Hide My Applist -> **App Manage** to find the package name of the app (e.g., com.xxxxx.xxxxx).

### Step 2: Install Termux
- Download Termux from [this link](https://github.com/termux/termux-app/releases).

### Step 3: Edit `target.txt`
1. Open Termux and run the following commands:
   ```
   pkg i tsu -y
   sudo nano /data/adb/tricky_store/target.txt
   ```
2. Add the package name to the bottom of the file (Use arrow down move the cursor to the bottom or swipe up to move the cursor).
3. Save (`CTRL+S`) and exit (`CTRL+X`).
4. Reboot (Next time you add a new app to /data/adb/tricky_store/target.txt, you don't need to reboot).
---

## Why Install These Modules?

- **Play Integrity Fix**: Bypass Play Integrity checks.
- **Tricky Store**: Hides bootloader status.
- **Zygisk Next**: Better root hiding.
- **Shamiko & Zygisk Assistant**: Enhance root hiding.

---

## Tested and is working on devices:
- Xiaomi 14T (Global)
- Redmi K60 Ultra 5G

---

## Images
![Image 1](https://github.com/user-attachments/assets/9095c40c-f120-4358-b7fa-58d34f73e1f0)
![Image 2](https://github.com/user-attachments/assets/856057ba-45a0-42de-8e9f-b8b4fa38d03d)
![Image 3](https://github.com/user-attachments/assets/65b9ccd2-98df-43c0-b530-2bda994d203e)
![Image 4](https://github.com/user-attachments/assets/32bed38b-407a-4f6c-b583-ae7ec3e6af9c)
![Image 5](https://github.com/user-attachments/assets/c383aab4-385d-4540-b3e1-15694ac43bf7)
![Image 6](https://github.com/user-attachments/assets/6cb09d52-a83b-4308-beab-364c1fc42baf)
![Image 7](https://github.com/user-attachments/assets/a98f5023-4862-40d7-8e8f-09620cd2c4b3)
![Image 8](https://github.com/user-attachments/assets/74596ec2-21f7-405d-85e0-0006c112499e)
![Image 9](https://github.com/user-attachments/assets/210824b1-00a3-4c3f-a8fe-ed45364a1479)
![Image 10](https://github.com/user-attachments/assets/d1fe51d7-650b-4f0c-8830-ff11adca6209)
![Image 11](https://github.com/user-attachments/assets/83963301-a37f-493c-b3d3-57978bb1eadc)
![Image 12](https://github.com/user-attachments/assets/4134ecbb-c89c-4e69-82ec-b00429ab0839)
![Image 13](https://github.com/user-attachments/assets/b59abb74-5f40-497e-affa-17c814925120)
