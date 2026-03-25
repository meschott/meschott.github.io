+++
date = '2026-03-14T22:12:30-04:00'
draft = true
title = 'Mitsubishicn105'
+++

I recently installed a new HVAC system at my house with 3 floors including a basement. The system is comprised of 3 mini-splits upstairs and a central basement-unit for the bottom two floors. The basement unit is controlled via a separate thermostat, and each mini split has its own remote control. Although, two of the mini-splits are on the same outdoor condenser so it's a split/linked system.

In terms of wifi-based control, I can connect the downstairs theromstat to HomeKit and the independent mini-split upstairs to  Mitsubishin's Comfort App (previously known as Kumo Cloud). 

Thankfully for me there is a great open solution for the mini-splits, https://github.com/echavet/MitsubishiCN105ESPHome. It seems my model numbers aren't sufficiently supported but all have the CN105 connector. I haven't worked with ESP32 boards but I have a couple of Raspeberry Pico boards that I do interface with through ESPHome in HomeAssistant. My enclosure skills are shit though.

After a bit more research I've found a more pre-packaged board off of Etsy which I am very tempted by, https://github.com/tinwer-group/mahtanar. I'm sure I could figure it out after awhile but I'd rather spend my time on other things right now. 


