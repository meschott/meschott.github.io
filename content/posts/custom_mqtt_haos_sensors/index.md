+++
date = '2025-11-15T23:27:01-05:00'
draft = true
title = 'Custom_mqtt_haos_sensors'
+++


In my spare time, I've continued to do some more fiddling with my Home Assistant. I managed to get my DB size under control (how to reference a prior post), and have spent time configure backups across my devices.

There are various automated systemd services that I have, where I want to know if they are failing. Home Assistant can send notifications to my phone, so I think it will work well for me. Here is a list of the various services I have that I would like to monitor in Home Assistant:

* bash script which uses rclone to backup my backup drive to Dropbox
* borg backups from my tower and my laptop to my backup drive
* python script which copies data from sqlite to postgres
* and maybe later...

  * proxmox monitoring things
  * job statuses from things that need to run on my tower with its larger ram and GPU
  * other backups!

After a little bit of research, it looks like using MQTT is a common way to do this. This is a pub/sub service. I've used AWS SNS in my experience, but I haven't done anything with MQTT. The concept in a nutshell AFAIK is you "Publish" into a Queue and then there can be many "Subscribers" to that queue. There is a Mosquito MQTT Add-on in Home Assistant which will suit my needs.

After initializing the client you can publish like so:
```python
result1 = client.publish(
    TEST_TOPIC, "test_running", qos=1, retain=True
)

```

I wonder if there is a convenient way to set this up where it will require minimal effort for any systemd service I setup.


