# RODECaster Pro II PipeWire Configuration

PipeWire and WirePlumber configuration for the RODE RODECaster Pro II on Linux.

## Features

- Automatically sets the **Pro Audio** profile exposing all channels
- Renames devices to match Windows naming convention:
  - **RODECaster Pro II - USB 1 Main** - Primary stereo input/output
  - **RODECaster Pro II - USB 1 Chat** - Dedicated channel for Discord/Skype/communication apps
  - **RODECaster Pro II - Multitrack** - 16-channel input for individual fader recording

## Installation

### Arch Linux / CachyOS / Manjaro (AUR)

```bash
# With yay
yay -S rodecaster-pro2-pipewire

# With paru
paru -S rodecaster-pro2-pipewire
```

### Manual Installation

```bash
# Clone the repository
git clone https://github.com/Jordan-Milner/rodecaster-pro2-pipewire.git
cd rodecaster-pro2-pipewire

# Build and install (Arch-based)
makepkg -si

# Or copy files manually (any distro)
sudo cp 50-rodecaster-pro2.conf /usr/share/pipewire/pipewire.conf.d/
sudo cp 51-rodecaster-pro2-rename.conf /usr/share/wireplumber/wireplumber.conf.d/
```

### After Installation

Restart PipeWire and WirePlumber:

```bash
systemctl --user restart wireplumber pipewire pipewire-pulse
```

Or simply reconnect your RODECaster Pro II.

## Audio Channels

After installation, your RODECaster Pro II will expose:

| Name | Type | Description |
|------|------|-------------|
| RODECaster Pro II - USB 1 Main | Output | Send audio to the RODECaster main mix |
| RODECaster Pro II - USB 1 Chat | Output | Send audio to the RODECaster chat channel (for Discord, etc.) |
| RODECaster Pro II - USB 1 Main | Input | Receive the main stereo mix from RODECaster |
| RODECaster Pro II - Multitrack | Input | Receive all 16 individual channels for multitrack recording |

## Troubleshooting

### Device not detected

Check if the device is recognized:

```bash
lsusb | grep -i rode
```

If not showing, try:
1. Reconnect the USB cable
2. Try a different USB port (preferably USB 3.0)
3. Check `journalctl -b | grep -i rode` for errors

### Channels not renamed

Verify WirePlumber loaded the config:

```bash
wpctl status
```

If names are still generic, restart WirePlumber:

```bash
systemctl --user restart wireplumber
```

## License

MIT
