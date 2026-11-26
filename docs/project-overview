# Project Overview

## Purpose
Build a self-hosted, privacy-focused security camera using a Raspberry Pi 5 and USB camera. Camera processing, recordings, and access should remain under the owner's control rather than depending on a third-party camera cloud.

## Initial proof of concept
- One USB camera
- Raspberry Pi OS Lite
- Motion for live streaming and motion detection
- Authenticated local live stream
- Motion-triggered local recording (next implementation milestone)

## Later capabilities
VPN remote access, browser dashboard, recording search and retention, notifications, multiple cameras, local object detection, continuous recording after storage expansion, and two-way audio.

## Design principles
1. Local-first operation.
2. Incremental development and validation.
3. Reproducible setup instructions.
4. Security by default and least privilege.
5. Clearly distinguish implemented, tested, planned, and experimental features.

## Current state
The Raspberry Pi 5 runs Raspberry Pi OS Lite. The Arducam USB camera is available as `/dev/video0`. Motion 4.7.0 provides a 1920×1080, 15 FPS live stream on port 8081. 
The Motion systemd service is enabled for automatic startup. Digest stream authentication has been enabled and tested from a Windows client. Movie output remains disabled.
