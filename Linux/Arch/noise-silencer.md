If you hear a static noise while nothing is playing you can follow this guide to cancel it.

## create a service
In this service we play a silent sin wave

0. Install `sox` on your linux:
```bash
sudo pacman -S sox
```
1. Create the service file
```bash
sudo nano /usr/lib/systemd/system/noise-silencer.service
```
2. Add the follwing content into the file:
```bash
[Unit]
Description=Keep USB Audio Alive Using sox

[Service]
ExecStart=/usr/bin/play -n -c2 synth sin gain -100

[Install]
WantedBy=default.target
```
3. Run:
```bash
sudo systemctl daemon-reload
```
4. Finally run the service and make in enable to run at restart
```bash
sudo systemctl enable --now noise-silencer
```

ref: https://destinmoulton.com/notes/howto/linux-usb-audio-keep-alive-service/
