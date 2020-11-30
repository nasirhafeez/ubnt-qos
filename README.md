# QoS Script for Ubiquiti Edge Router

This script is the implementation of the idea presented in [this](https://community.ui.com/questions/Script-for-QOS/0d1a2c1a-15ff-4a0f-b1c6-7d9d8902eedc) Unifi community post. It does the following:

1. Disables Smart Queue QoS
2. Runs a speed test
3. Inputs those values into the Smart Queue
4. Re-enables Smart Queue

It has been tested successfully on EdgeRouter X v2.0.9.

Replace the value of `wanif` parameter in the script with your current WAN interface.

This script should be added to `/config/scripts` and made executable:

```
chmod +x /config/scripts/qos
```

The following commands can be used to run it as a scheduled task/cron job (every 15 min):

```
configure

set system task-scheduler task qos-update executable path /config/scripts/qos
set system task-scheduler task qos-update interval 15

commit; save
```

Instructions for downloading speedtest-cli and running scripts on Edge Routers are given [here](https://gist.github.com/nasirhafeez/9a2b9d236eaa48fc6d482f8aee603145)
