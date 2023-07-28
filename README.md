# Linux Configs
## Context
I've been using different Linux distros (plain Debian, Ubuntu, Manjaro, EndevourOS, PopOS, etc) for several years. During this time I had several issues that were similar and, from mine understanding, are quite common. So I created this repo for future myself, who will debug some strange Linux behavior for several hours to find outm that fix is a single console command.

### My Hardware/Software
Trimmed neofetch response: 
- OS: Ubuntu 23.04 x86_64
- Host: ASUS TUF Gaming FX505DY_FX505DY 1.0 
- Resolution: 1920x1080 
- DE: GNOME 44.2 
- CPU: AMD Ryzen 5 3550H 
- GPU1: AMD ATI Radeon RX 560X 
- GPU2: AMD ATI Radeon Vega 7
- Memory: 8GB 
##  Configs
### Integrated/Dedicated GPU
#### Encountered issue:
- Steam GUI crashes and restarts indefinitely while using dedicated GPU (in my case Radeon RX 560X)
#### Fix
If your distro doesn't have dedicated GPU switch (or you are using pair of AMD GPUs) - you'll have to edit `.desktop` files to specify preferred GPU. 
By default `.desktop` files are stored in `/usr/share/applications/`.

At the end of the config this two lines could be added/edited: 
```
PrefersNonDefaultGPU=true
X-KDE-RunOnDiscreteGpu=true
```
Steam application has by default both set tot true, so you might want to switch both to false to fix this issue.

## Touchpad
By default many distros disable touchpad while typing. While it could be useful due to lack of drivers for proper palm rejection for some of the touchpads, I found it quite annoying in some applications, that are not programmed to be used only using shortcuts. 

From what I read, the option to enable touchpad while typing has to be in the Setting application, on any distro I haven't seen this option in GUI without installing additional software.

For GNOME the solution is this command: 
```
gsettings set org.gnome.desktop.peripherals.touchpad disable-while-typing false
```
which enables touchpad while typing.