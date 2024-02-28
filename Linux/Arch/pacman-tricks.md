# Pacman Tricks




### Sort installed packages by size

```bash
pacman -Qi | egrep '^(Name|Installed)' | cut -f2 -d':' | paste - - | column -t | sort -nrk 2 | grep MiB | less 
```

### Remove unneeded dependencies
```bash
sudo pacman -R $(pacman -Qdtq)
```
### Invalid signiture:

```bash
pacman-key --populate archlinux
```
##### Another solution that may work:

```bash
pacman -Sy archlinux-keyring && pacman -Su
```
