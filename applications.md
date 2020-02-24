# Aplications

## Pacaur

AUR package manager for arch.
`sudo pacman -S pacaur`

## Numlockx

Used to turn numlock on by default.
`sudo pacman -S numlockx`

## Dolphin

File manager with integrated terminal.
`sudo pacman -S dolphin konsole qt5ct`

# Rofi

DMenu replacement.
`sudo pacman -S rofi`

# Rofimoji (Emoji Picker)

Emoji picker utilizing rofi.
`sudo pacman -S rofimoji`

## i3status-rust

Customizable resource light i3 status bar.
`pacaur -S i3status-rust`

And to remove rust again if not needed: `pacaur -Rs rust`

## Font Awesome 4

Font for many symbols and logos.
`pacaur -S ttf-font-awesome-4`

## Powerline

Graphical improvement for prompt and vim status line.
`sudo pacman -S powerline`


## Advanced Operating Systems

Commands:
./bfdocker.sh "cd /source/build && /source/hake/hake.sh -s /source"
./bfdocker.sh "cd /source/build && make armv8_aos_m0_image.efi"

picocom -b 115200 -f n /dev/ttyUSB0
~/projects/aos/hand-out/tools/imx8x/bf-boot.sh --bf ~/projects/aos/hand-out/milestone0_test_image

### picocom

Terminal emulation program.
`sudo pacman -S picocom`

### Docker

`sudo pacman -S docker`
`sudo systemctl start docker`
`sudo usermod -aG docker $USER`
Relog to update group information.

### Universal Update Utility (UUU)

1. Required usb python lib: `sudo pacman -S python-pyusb`
2. `wget -P $HOME/bin https://github.com/NXPmicro/mfgtools/releases/download/uuu_1.3.102/uuu`
3. Add $HOME/bin to $PATH in .bashrc: `export PATH="$HOME/bin:$PATH"`

### UDEV Rule

Allows any user to access UART of the Toradex board.

```
sudo cat > /etc/udev/rules.d/60-colibri.rules << EOF
# USB OTG
SUBSYSTEM=="usb", ATTR{idVendor}=="0525", ATTR{idProduct}=="4026", MODE="0666"
# Serial USB device
SUBSYSTEM=="usb", ATTR{idVendor}=="0403", ATTR{idProduct}=="6001", MODE="0666"
# Serial TTY device
SUBSYSTEM=="tty", ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6001", MODE="0666"
EOF
sudo udevadm control --reload && sudo udevadm trigger
```
