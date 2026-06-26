# MacOS Sound Theme

MacOS sounds for Linux. Sounds were sourced from:

https://bigsur-sounds.itsnoahevans.co.uk/

The full Sound Naming Specification:

http://0pointer.de/public/sound-naming-spec.html

## Installation

Run `meson` to configure the build environment and then `ninja install` to install

```bash
meson build --prefix=/usr
cd build
sudo ninja install
```

This installs the theme to `/usr/share/sounds/macos`.

## Enabling the theme

The theme is named `macos`. Sounds are played by libcanberra, which reads the
active theme from your GTK settings or your desktop's settings daemon. Pick the
section for your setup below. Most desktops also need event sounds turned on, so
each example enables them too.

### GTK

Set the theme directly in your GTK config. This is read by libcanberra on
desktops that do not manage the setting themselves (window managers, sway, etc).

For GTK 3 and GTK 4, add to `~/.config/gtk-3.0/settings.ini` and
`~/.config/gtk-4.0/settings.ini`:

```ini
[Settings]
gtk-sound-theme-name = macos
gtk-enable-event-sounds = true
gtk-enable-input-feedback-sounds = true
```

For GTK 2, add to `~/.gtkrc-2.0`:

```
gtk-sound-theme-name = "macos"
gtk-enable-event-sounds = true
gtk-enable-input-feedback-sounds = true
```

### GNOME

```bash
gsettings set org.gnome.desktop.sound theme-name 'macos'
gsettings set org.gnome.desktop.sound event-sounds true
gsettings set org.gnome.desktop.sound input-feedback-sounds true
```

### Cinnamon

```bash
gsettings set org.cinnamon.desktop.sound theme-name 'macos'
gsettings set org.cinnamon.desktop.sound event-sounds true
gsettings set org.cinnamon.desktop.sound input-feedback-sounds true
```

### XFCE

```bash
xfconf-query -c xsettings -p /Net/SoundThemeName -n -t string -s macos
xfconf-query -c xsettings -p /Net/EnableEventSounds -n -t bool -s true
xfconf-query -c xsettings -p /Net/EnableInputFeedbackSounds -n -t bool -s true
```

The `-n` flag creates the property if it does not exist yet.

## Testing

Play a sound from the theme without changing any config:

```bash
canberra-gtk-play --property=canberra.xdg-theme.name=macos -i bell
```

After switching the theme you may need to log out and back in for all
applications to pick up the change.
