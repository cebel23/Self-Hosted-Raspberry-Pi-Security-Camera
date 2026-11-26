# Development Log

## 2026-11-25 — Documentation baseline

### Decisions
- Project name: Self-Hosted Raspberry Pi Security Camera.
- License: MIT.
- Audience: hobbyists and technical recruiters.
- Initial deployment: one camera; multiple cameras may be added later.
- Access goal: local and remote.
- Long-term recording goal: motion-triggered and continuous, but motion-triggered only during the initial build.
- Continuous recording deferred until storage is upgraded.
- Audio deferred.

### Working implementation
- Raspberry Pi 5 running Raspberry Pi OS Lite.
- Hostname: PI_HOSTNAME.
- SSH administration from Windows works.
- Arducam 1080p USB camera detected at `/dev/video0`.
- Motion 4.7.0 installed.
- Live stream configured at 1920×1080 and 15 FPS.
- Motion systemd service enabled for automatic startup.
- Live stream on TCP port 8081.
- Digest stream authentication enabled and tested.
- Motion runs as dedicated `motion` user with video-group membership.
- Recording output remains disabled.

### Recording baseline
```ini
target_dir /var/lib/motion
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
```

### Next milestone
Configure and test motion-triggered recording only. Do not enable continuous recording in the initial build.

## Future entry template

### YYYY-MM-DD — Milestone title
**Goal:** What was being implemented?

**Changes:** What configuration, code, or hardware changed?

**Validation:** What commands or tests demonstrated success?

**Problems and resolution:** What failed and how was it fixed?

**Decisions:** What tradeoffs or future implications were identified?

**Next steps:** What remains?
