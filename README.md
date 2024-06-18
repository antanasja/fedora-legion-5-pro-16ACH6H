# fedora-legion-5-pro-16ACH6H
Knowledge base on running Fedora 40 on Legion 5 pro (16ACH6H)

## How to's
- Nvidia drivers: https://rpmfusion.org/Howto/NVIDIA

## Issues

### Microphone
At least on ALC287 internal microphone volume is boosted too much. To solve this change some values in `/usr/share/alsa-card-profile/mixer/paths/analog-input-internal-mic.conf`:

```diff
[Element Internal Mic Boost]
required-any = any
switch = select
-volume = merge
+volume = zero
override-map.1 = all
override-map.2 = all-left,all-right

[Option Internal Mic Boost:on]
name = input-boost-on

[Option Internal Mic Boost:off]
name = input-boost-off

[Element Int Mic Boost]
required-any = any
switch = select
-volume = merge
+volume = zero
override-map.1 = all
override-map.2 = all-left,all-right
```