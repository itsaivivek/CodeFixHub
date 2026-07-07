# Fix: GRUB Default OS Changes Ignored on Ubuntu/elementary OS (UEFI)

A comprehensive guide to fixing the issue where changes to `/etc/default/grub` or **Grub Customizer** (like setting Windows as the default boot entry) are completely ignored during startup on modern UEFI systems.

---

## 🔍 The Problem

When you modify `/etc/default/grub` and run `sudo update-grub`, Linux generates a fresh configuration file at `/boot/grub/grub.cfg`. 

However, many modern UEFI motherboards bypass this local file entirely. Instead, they read from a static, duplicated GRUB configuration file tucked away inside the hidden **EFI System Partition (ESP)** (usually under `/boot/efi/EFI/ubuntu/`). Because the motherboard executes this static EFI file at startup, any structural or index modifications you make on your active operating system partition never take effect.

---

## 🛠️ The Solution: Force-Copy Your New GRUB Layout

This method forces your motherboard to read your newly updated settings by manually overwriting the static file inside the active EFI directory.

### Step-by-Step Instructions

1. **Boot** into your Ubuntu-based distribution (e.g., elementary OS).
2. **Open** your terminal.
3. **Edit** your configuration file to your preference (e.g., setting `GRUB_DEFAULT=2` for Windows):
   ```bash
   sudo nano /etc/default/grub
   ```
   *(Save and exit the text editor).*

4. **Generate** the fresh configuration layout:
   ```bash
   sudo update-grub
   ```

5. **Overwrite** the motherboard's active boot folder with your newly generated file:
   ```bash
   sudo cp /boot/grub/grub.cfg /boot/efi/EFI/ubuntu/grub.cfg
   ```

6. **Restart** your computer. Your default entry selection or custom order will now display correctly.

---

## ⚖️ Pros and Cons of This Method

### Pros
* **Immediate Fix:** Solves the stubborn issue where standard terminal commands fail.
* **No Extra Tools:** Does not require installing third-party boot-repair applications.
* **High Success Rate:** Works reliably across various motherboards that hardcode the EFI path.

### Cons
* **Manual Upkeep:** Future Linux kernel updates or system upgrades may overwrite or bypass this file, requiring you to run the `cp` command again.
* **Risk of Desync:** The main system partition and the EFI partition can fall out of sync over time.

---

## 🔄 Alternative Way

If you prefer a permanent solution that fixes the underlying pathing issue without manual copying, you can reinstall GRUB directly to your EFI partition.

Run the following command (replace `/dev/sdX` with your main drive letter, e.g., `/dev/sda`):

```bash
sudo grub-install /dev/sdX
sudo update-grub
```

This registers the correct operating system paths directly to your motherboard's NVRAM, allowing future system updates to sync automatically.
