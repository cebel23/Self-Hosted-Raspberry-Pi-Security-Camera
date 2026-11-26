# Self-Hosted-Raspberry-Pi-Security-Camera
A privacy-focused, self-hosted security camera proof of concept built around a Raspberry Pi 5, Raspberry Pi OS Lite, an Arducam 1080p USB camera, and Motion.  The goal is to provide locally managed camera monitoring and motion-triggered recording without depending on a third-party camera cloud service.

> **Current status:** Initial camera setup and authenticated live streaming are working. Motion-triggered recording, VPN remote access, recording management, and a dashboard are planned—not yet completed.

## Goals
- Keep camera processing and recordings under the owner's control.
- Provide live video on the local network.
- Require authentication to view the stream.
- Record video only when motion is detected during the initial phase.
- Manage recordings locally with configurable retention.
- Add VPN-based remote access without exposing camera ports directly to the public internet.
- Keep the design extensible for more cameras and future features.
- Document the build so others can reproduce it.

## Current implementation

| Component | State |
|---|---|
| Raspberry Pi 5 / Raspberry Pi OS Lite | In use |
| SSH administration | Working |
| Arducam 1080p USB camera | Detected as `/dev/video0` |
| Motion | Version 4.7.0 installed |
| Live stream | Working at 1920×1080, 15 FPS |
| Motion systemd startup | Enabled |
| Stream authentication | Digest authentication enabled and tested |
| Motion-triggered recording | Not enabled yet |
| Continuous recording | Deferred until storage upgrade |
| VPN remote access / dashboard | Planned |

## Hardware
- Raspberry Pi 5
- Arducam 1080p Low Light USB camera
- microSD card (OS and current development storage)
- Raspberry Pi cooling solution

A dedicated USB SSD is deferred. The initial build focuses on validating basic camera functionality and motion-triggered recording before adding storage hardware.

## Software
| Software | Role |
|---|---|
| Raspberry Pi OS Lite | Operating system |
| Linux / systemd | System and service management |
| OpenSSH | Remote administration |
| V4L2 | Linux video-device interface |
| Motion 4.7.0 | Live stream and planned motion detection/recording |

## Current architecture

```text
Arducam USB camera
        |
        v
Linux video device (/dev/video0)
        |
        v
Motion service on Raspberry Pi 5
        |
        +---- Authenticated live stream (TCP 8081)
        |
        +---- Future: motion-triggered local recordings
        |
        v
Local network clients
```

The Raspberry Pi is the camera server. Client computers view the stream; they are not responsible for keeping the camera running or recording.

## Current camera configuration

| Setting | Value |
|---|---|
| Camera device | `/dev/video0` |
| Resolution / frame rate | 1920×1080 / 15 FPS |
| Stream port | 8081 |
| Stream authentication | Digest; tested successfully |
| Recording directory | `/var/lib/motion` |
| Movie output | Currently off |
| Picture output | Off |

Do not publish actual LAN addresses, usernames, passwords, or unredacted configuration files.

## Recording design

The initial recording mode is **motion-triggered only**. Continuous recording is postponed until a storage upgrade. The design target is a configurable maximum of approximately two minutes per individual event clip. This is a project preference to validate, not a claim about Motion's inherent limits. Long-event and file-segmentation behavior will be tested.

## Security principles
- Keep recordings local by default.
- Require authentication for the camera stream.
- Keep administrative interfaces restricted.
- Never commit credentials, private keys, or secrets.
- Do not expose camera services directly to the public internet.
- Use a VPN for future remote access.
- Digest authentication is access control, not transport encryption.

## Roadmap
1. Initial setup — **complete**: OS, SSH, camera detection, Motion installation, live stream, automatic service startup.
2. Stream security — **initial implementation complete**: Digest authentication tested; continue reviewing network exposure.
3. Motion recording — **next**: enable and test motion-triggered clips.
4. Recording management: organization, retention, cleanup, storage monitoring.
5. Remote access: VPN-based access.
6. Dashboard: live view, event history, playback, camera health, storage status.
7. Enhancements: notifications, local object detection, multiple cameras, continuous recording after storage expansion, two-way audio.

## Repository layout

```text
.
├── README.md
├── LICENSE
├── config/motion.conf.example
├── docs/
├── diagrams/
├── screenshots/
└── scripts/
```

## License
MIT. See [LICENSE](LICENSE).
