Definition of platform required for room scanner h/w, assuming using Raspi4B

# OS Base image
Rasbian Buster: 2020-02-13-raspbian-buster

## Headless setup
After creating the image onto the SD card, add the following files into the `boot` partition

### Enable SSH
Put an empty file with the filename `ssh`

### Enable wifi
Put a file with the filename `wpa_supplicant.conf`
Containing the following (note swap in wifi credentials here):

```
country=US
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
    ssid="<Enter wifi network name here>"
    psk="<Enter wifi password here>"
}
```

## General OS setup

When the SD card is in the RasPi4, SSH in:
```
sudo apt update
sudo apt upgrade
```

## Dependencies

### Kivy

```
sudo apt install libsdl2-dev libsdl2-image-dev libsdl2-mixer-dev libsdl2-ttf-dev pkg-config libgl1-mesa-dev libgles2-mesa-dev python3-setuptools libgstreamer1.0-dev git-core gstreamer1.0-plugins-{bad,base,good,ugly} gstreamer1.0-{omx,alsa} python3-dev libmtdev-dev xclip xsel libjpeg-dev
python3 -m pip install --upgrade --user pip setuptools
python3 -m pip install --upgrade --user Cython==0.29.10 pillow
sudo pip3 install kivy
```
