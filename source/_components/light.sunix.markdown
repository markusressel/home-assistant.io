---
layout: page
title: "Sunix LED Strip Controller"
description: "Access and control your LED stripes attached to a Sunix RGBWW LED Controller."
date: 2018-11-01 22.04
sidebar: true
comments: false
sharing: true
footer: true
logo: sunix_rgbw_led.png
ha_category: Light
ha_iot_class: "Local Polling"
ha_release: 0.84
---

TODO: write some config examples

## {% linkable_title Example Configuration %}

```yaml
light:
  - platform: sunix_rgbw_led
    devices:
      strip1:
        host: "192.168.2.150"
```

{% configuration %}
devices:
  required: true
  description: List of Sunix Controller devices.
  type: map
  keys:
    hass_device_name:
      description: Name of the device in Home Assistant.
      required: true
      type: map
      keys:
        name:
          description: A friendly name for the device.
          required: false
          type: string
        host:
          description: The IP/Host of the Controller.
          required: true
          type: string
        max_brightness:
          description: A limit on the maximum brightness of the light.
          required: false
          type: integer
          default: 255
        calibration_factor:
          description: Node to define color channel calibration factors (value in [0..1]).
          required: false
          type: map
          red: 
            description: The factor to apply to the **red** color channel.
            required: false
            type: float
            default: 1
          green: 
            description: The factor to apply to the **green** color channel.
            required: false
            type: float
            default: 1
          blue: 
            description: The factor to apply to the **blue** color channel.
            required: false
            type: float
            default: 1
          warmwhite: 
            description: The factor to apply to the **cold white** color channel.
            required: false
            type: float
            default: 1
          coldwhite: 
            description: The factor to apply to the **warm white** color channel.
            required: false
            type: float
            default: 1
{% endconfiguration %}

### {% linkable_title Initial setup %}
<p class='note'>
Before trying to control your light through Home Assistant, you have to setup your controller using 
a compatible app such as the **Magic Home** app 
([Android](https://play.google.com/store/apps/details?id=com.Zengge.LEDWifiMagicHome), [IOS](https://itunes.apple.com/de/app/magic-home-wifi/id944574066)
or the **Magic Home Pro** app (which is also free - dont ask) ([Android](https://play.google.com/store/apps/details?id=com.zengge.wifi), [IOS](https://itunes.apple.com/de/app/magic-home-pro/id1187808229))
or even the **S Panel** app ([Android](https://play.google.com/store/apps/details?id=com.sunix.wifipro), [IOS](https://itunes.apple.com/us/app/s-panel/id1261793813)).
You can also find out the IP address of the controller in the Magic Home Pro app (after it has been connected to 
your local WiFi of course) using the menu option "Device Manager". A list of all the connected controllers should be 
shown and a tap on the controller you are interested in will show additional details like the IP address.
</p>

### {% linkable_title Compatibility %}

The network protocol used by the Sunix controller is used in a variety of devices.

## {% linkable_title Examples %}

In this section you find some real-life examples of how to use this component.

### {% linkable_title Full configuration %}

This example shows how you can use the optional configuration options.

```yaml
# Example configuration.yaml entry
light:
  - platform: sunix_rgbw_led
    devices:
      strip1:
        name: "LED Stripe 1"     # optional
        host: "192.168.2.150"
        max_brightness: 125      # optional
        calibration_factor:      # optional
          red: 0.39              # optional
          green: 0.157           # optional
          blue: 0.196            # optional
          warmwhite: 1           # optional
          coldwhite: 1           # optional
```

### {% linkable_title Multiple bulbs %}

This example shows how you can add multiple bulbs in your configuration.

```yaml
light:
- platform: sunix_rgbw_led
  devices:
    strip1:
      name: "LED Stripe 1"     # optional
      host: "192.168.2.150"
      max_brightness: 125      # optional
    strip2:
      name: "LED Stripe 2"     # optional
      host: "192.168.2.151"
      max_brightness: 125      # optional
      calibration_factor:      # optional
        red: 0.39              # optional
        green: 0.157           # optional
        blue: 0.196            # optional
        warmwhite: 1           # optional
        coldwhite: 1           # optional
```
