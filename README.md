<div align="center">

# 🎉 Yay Polybar

[![Arch Linux](https://img.shields.io/badge/Arch%20Linux-blue?logo=arch-linux\&logoColor=white)](https://archlinux.org/)
[![Polybar](https://img.shields.io/badge/Polybar-black?logo=polybar\&logoColor=white)](https://github.com/polybar/polybar)
[![AUR Helper: yay](https://img.shields.io/badge/AUR%20Helper-yay-success?logo=arch-linux\&logoColor=white)](https://github.com/Jguer/yay)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)

*A simple Polybar script to display available Arch Linux updates with click actions for notifications and GUI-based package selection.*

</div>

---

## ✨ Features

* 📦 **Update Count** – Displays the total number of updates available.
* 🔔 **Click Actions** (optional):

  * **Left-click** → Show a desktop notification listing update candidates.
  * **Right-click** → Launch a GUI to select which packages to update, then upgrade them via `yay`.

---

## 📸 Screenshots

### Polybar Module

<p align="center">
  <img src="https://i.imgur.com/ZMap2mN.png" alt="Polybar Module With Updates" width="50"/>
</p>

### GUI Package Selection

<p align="center">
  <img src="https://i.imgur.com/mXIdvvf.png" alt="Package Update GUI" width="500"/>
</p>

---

## 📦 Dependencies

* **Required**

  * [`yay`](https://github.com/Jguer/yay) – AUR helper for Arch Linux

* **Optional (for click actions)**

  * `i3wm` – Window manager (used to run scripts)
  * `notify-send` – Desktop notifications
  * `zenity` – Graphical package selection dialog
  * `termite` – Terminal emulator for running updates interactively

---

## 🚀 Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/yourusername/yay-polybar.git ~/code/yay-polybar
   cd ~/code/yay-polybar
   ```

2. **Make scripts executable**

   ```bash
   chmod +x updates-arch-yay.sh notify-updates.sh prompt-updates.sh
   ```

3. **Add to Polybar config**
   Insert the following block into your `~/.config/polybar/config.ini`:

   ```ini
   [module/updates]
   type = custom/script
   exec = ~/code/yay-polybar/updates-arch-yay.sh
   interval = 600
   click-left = i3-msg exec ~/code/yay-polybar/notify-updates.sh
   click-right = i3-msg exec ~/code/yay-polybar/prompt-updates.sh
   ```

4. **Reload Polybar**
   Restart Polybar or reload your config to apply the changes.

---

## 🖱️ Usage

* **Left Click → Notify Updates**
  Displays a system notification with the list of available package updates.

* **Right Click → Prompt Updates**
  Opens a `zenity` dialog to select packages for updating, then triggers their upgrade via `yay`.

---

## 🪟 i3wm Integration

To display the update terminal as a floating, centered window in i3:

```i3 title="~/.config/i3/config"
for_window [instance="^package-update$" class="^Termite$"] floating enable, move position center
```

---

<div align="center">

💡 **Tip:** With **Yay Polybar**, staying up-to-date on Arch Linux is just a glance and a click away!

</div>
