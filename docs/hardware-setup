# Hardware Setup

## Current bill of materials

| Item | Current selection | Notes |
|---|---|---|
| Single-board computer | Raspberry Pi 5 | Main camera server |
| Camera | Arducam 1080p Low Light USB camera | USB connection |
| OS storage | microSD card | Current development storage |
| Cooling | Raspberry Pi standard cooler | Installed |
| Network | Home LAN | SSH and local stream viewing |

## Camera identification
The camera is currently configured in Motion as `/dev/video0`. Confirm the device node on each target system rather than assuming it will always be the same.

```bash
lsusb
ls -l /dev/video*
v4l2-ctl --list-devices
v4l2-ctl --list-formats-ext -d /dev/video0
```

Install `v4l-utils` if `v4l2-ctl` is unavailable.

## Storage
The initial build uses the microSD card and is limited to motion-triggered recording during development. A dedicated USB SSD is planned before continuous recording is introduced.
