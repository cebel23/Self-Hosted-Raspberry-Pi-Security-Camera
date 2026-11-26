# Recording and Storage

## Initial strategy
The initial implementation will use motion-triggered recording only. Continuous recording is postponed until a dedicated storage upgrade.

The design target is a configurable maximum of approximately two minutes per individual event clip. This is a project preference to test, not a confirmed current capability or an inherent Motion limit.

## Current state
Movie output is disabled:

```ini
movie_output off
```

Observed baseline:

```ini
event_gap 60
pre_capture 3
post_capture 0
movie_max_time 60
movie_quality 45
movie_codec mkv
movie_filename %t-%v-%Y%m%d%H%M%S
target_dir /var/lib/motion
```

Motion-triggered recording has not yet been validated.

## Planned implementation
- Enable Motion movie output.
- Verify a supported container/codec combination.
- Tune motion sensitivity in the intended camera environment.
- Configure pre-motion and post-motion capture.
- Test long motion events and file segmentation.
- Confirm playback on Windows.
- Implement retention and cleanup before unattended use.

## Storage
The current system uses a microSD card. Initial testing will be limited to motion-triggered clips and disk monitoring. A dedicated USB SSD is planned before continuous recording is added.

## Test log

| Test | Result | Notes |
|---|---|---|
| Motion event detected | Not tested | |
| Video file created | Not tested | |
| Clip plays on Windows | Not tested | |
| Clip duration behavior | Not tested | |
| Retention cleanup | Not tested | |
