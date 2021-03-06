# Yay Polybar 

A script that shows the total available updates for Arch Linux using `yay`.
Includes optional click actions to display a notification of available updates
and another to display a GUI list of available packages and trigger the update
of those the user selects.

## Screenshot Previews
### Module
![Polybar Module With Updates](https://i.imgur.com/ZMap2mN.png)

### Package Update GUI
![Package Update GUI](https://i.imgur.com/mXIdvvf.png)


## Dependencies

Requires `yay`.

Optional left and right click actions required:
  * `i3wm`, window manager
  * `notify-send`, broadcast notifcation
  * `zenity`, display table for package selection
  * `termite`, terminal to execute updates with output

## Module

```ini
 [module/updates]
 type = custom/script
 exec = ~/code/yay-polybar/updates-arch-yay.sh
 interval = 600
 click-left = i3-msg exec ~/code/yay-polybar/notify-updates.sh
 click-right = i3-msg exec ~/code/yay-polybar/prompt-updates.sh
```
### Notify Updates

Left clicking on the module will trigger a system notifcation with a list of
package names for which there are currently updates available.

### Prompt for Updates

Right clicking on the module will trigger the display of a table to allow the
selection of which packages to upgrade, and automatically start their upgrade
through `yay`.

## i3 Configuration

Show package updates from Polybar in floating window

```
 for_window [instance="^package-update$" class="^Termite$"] floating enable, move position center 
```
