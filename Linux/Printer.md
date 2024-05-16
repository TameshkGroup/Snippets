To make pritners work in linux:
```bash
sudo pacman -S cups
sudo systemctl enable --now cups
```

For mangaging it:

```bash
sudo pacman -S system-config-printer
```
Install the following driver as well. You can find it model [here](https://wiki.archlinux.org/title/CUPS/Printer-specific_problems)

```bash
yay -S epson-inkjet-printer-escpr2
```

For my printer I set the following settings in `system-config-pritner`:

Printer Options > Print Quality > Epson Photo Quality Ink Jet-High
Media Size:  6x4 | 6x4 borderless

By setting these values no don't need to set it on every print.



