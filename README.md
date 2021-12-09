# OBS settings for linux

## GOPRO webcam

https://github.com/jschmid1/gopro_as_webcam_on_linux

### change devices number in scripts

```
sudo nano `which gopro` 
```

this line

```
module_cmd="modprobe v4l2loopback exclusive_caps=1 card_label='GoPro' video_nr=2 devices=3"
```

### start webcam daemon

```
sudo gopro webcam  -u eehah5ru -r 1080
```

### start ffmpeg sinking to vodeo device

use output of gopro script

## OBS

start virtual source in ppulse audio

```
pactl load-module module-virtual-source source_name=Remap-Source master=Virtual-Speaker.monitor
```

and then

```
pactl load-module module-null-sink sink_name=Virtual-Speaker sink_properties=device.description=Virtual-Speaker
```

then select virtual devices in zoom etc.

in obs selevt `monitor on` in audio properties.

in obs select proper monitor device.

## troubleshooting

check v4l devices

```
v4l2-ctl --list-devices
```

check who is locking device

```
lsof /dev/video42 
```



