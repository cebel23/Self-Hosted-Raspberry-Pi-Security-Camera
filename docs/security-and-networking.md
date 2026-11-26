# Security and Networking

## Current measures
- Motion stream Digest authentication is enabled and tested.
- Camera credentials are separate from the Raspberry Pi SSH login.
- Motion web control is configured for localhost access.
- Motion runs under its dedicated `motion` account, not root.
- The configuration file was restricted to root ownership and the `motion` group (mode `640`) during setup.

Verify service identity:

```bash
id motion
systemctl show motion -p User -p Group
```

The current system reported `uid=102(motion)`, `gid=105(motion)`, membership in group `video`, and `User=motion`. Numeric IDs can differ on other installations.

## Authentication is not encryption
Digest authentication controls access but does not encrypt the video transport. Treat the current HTTP stream as suitable only for a trusted local network.

## Remote access plan
Remote access is a project requirement but is not yet implemented. The planned approach is VPN-based access. Do not forward Motion stream port `8081` or administrative port `8080` directly to the public internet.

## Credential handling
- Use unique camera-stream credentials.
- Do not reuse the Linux login password.
- Never put credentials in Git, screenshots, or public issue reports.
- Keep the live `motion.conf` out of the repository if it contains credentials.
- Publish only a sanitized example configuration.
