# Camera and Motion Setup

## Current working configuration
Motion version: `4.7.0`. The Arducam USB camera is configured as `/dev/video0`, with 1920×1080 resolution and 15 FPS. The live stream uses TCP port `8081`. Digest authentication has been enabled and tested from a Windows browser.

## Service management

```bash
sudo systemctl enable motion
sudo systemctl start motion
sudo systemctl status motion --no-pager
sudo systemctl restart motion
```

## Inspect relevant settings

```bash
sudo grep -nE '^(daemon|video_device|width|height|framerate|stream_port|stream_localhost|webcontrol_port|webcontrol_localhost|picture_output|movie_output|target_dir)' /etc/motion/motion.conf
```

## Current known values

| Setting | Value |
|---|---|
| `video_device` | `/dev/video0` |
| `width` / `height` | `1920` / `1080` |
| `framerate` | `15` |
| `stream_port` | `8081` |
| `stream_localhost` | `off` |
| `webcontrol_localhost` | `on` |
| `target_dir` | `/var/lib/motion` |
| `picture_output` | `off` |
| `movie_output` | `off` |

Stream authentication settings are intentionally omitted. Configure a unique camera username and password locally. Never publish credentials.

## Recording baseline before recording is enabled

```ini
threshold 1500
minimum_motion_frames 1
event_gap 60
pre_capture 3
post_capture 0
picture_output off
movie_output off
movie_max_time 60
movie_quality 45
movie_codec mkv
movie_filename %t-%v-%Y%m%d%H%M%S
target_dir /var/lib/motion
```

These values describe the observed baseline, not the final recording configuration.

## Validation
1. Confirm Motion is active.
2. Open the stream from a trusted LAN client.
3. Confirm the browser requests camera credentials.
4. Verify the live feed.
5. Reboot and confirm Motion starts automatically.
