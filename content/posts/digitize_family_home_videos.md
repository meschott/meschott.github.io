+++
date = '2026-03-22T13:15:43-04:00'
draft = false
title = 'Digitize_family_home_videos'
+++

I have a bunch of VHS and DVDs containing old home videos which I would like to digitize to my computer and probably copy up to cloud object storage since my home storage capacity is pretty limited and to be more easily shareable with my family. I found a VHS/DVD player hybrid, made by Daewoo, unused somewhere and took it home for this project.

I bought this off of Amazon, https://www.amazon.com/dp/B0FJYGBR4J?ref=ppx_yo2ov_dt_b_fed_asin_title, which has worked well so far.

I fired up the VHS/DVD player and popped in a tape with that old satisfying tape-loading sound. Upon hooking up the RCA cables and plugging in the USB to my Linux computer, `lsusb` showed the following `Bus 001 Device 009: ID 534d:0021 MacroSilicon MS210x Video Grabber [EasierCAP]`. Yay!

This command then confirmed an audio source was automatically loaded by the driver, 
```
pactl list sources | grep -A3 "Name:"

        Name: alsa_input.usb-MACROSILICON_USB_Video_20200909-02.analog-stereo
        Description: MS210x Video Grabber [EasierCAP] Analog Stereo
        Driver: module-alsa-card.c
        Sample Specification: s16le 2ch 48000Hz

```

My plan was to try and rip these things through VLC. I am not that well versed in audio/video i/o btw, so I was pinging the clanker lots of questions.

I had to install v4l-utils, ffmpeg, and alsa-utils packages on my machine. VLC was already installed.
`pacman -S vlc vlc-plugins-extra v4l-utils ffmpeg alsa-utils`

After this command, vlc opened and video played! Lots of noises from the VHS player though, so hopefully this thing lasts a little while longer...
`vlc v4l2:///dev/video0 :input-slave=pulse://alsa_input.usb-MACROSILICON_USB_Video_20200909-02.analog-stereo`

```
ffmpeg -f v4l2 -input_format yuyv422 -video_size 720x480 -framerate 30 \
  -i /dev/video0 \
  -f pulse -i alsa_input.usb-MACROSILICON_USB_Video_20200909-02.analog-stereo \
  -c:v ffv1 -c:a flac \
  output.mkv
```

So now it seems I need to make a plan. Recording happens at normal speed, so this is going to be an async process I will run on the side. Tentatively:
  1. Dedicate my second monitor to this for a week or so
  2. Sort the tapes and dvds... I have 17 tapes and 23 dvds.
  3. Start with the dvds since there seems to be some overlap.
  4. Find the right copy settings
  5. Copy to local
  6. Organize, split, tag?
  7. Rip a couple more maybe
  8. Organize, split, tag
  9. After a few push to the cloud object storage
  10. Repeat til DVDs are done
  11. Organize again
  12. Start ripping some VHSs and compare content and quality
  13. Assess cloud costs and storage size
  14. Share with siblings


  Ok so very quickly I realized there is a lot of overlap between the dvds and vhss. I am going to switch to dvds but I amm going to use my old external disk drive for that which will be able to burn dvds much faster. Now I kind of hope it isn't completely overlapped or else I am out 20 bucks! Check back in a few days when I've ripped all of the dvds.