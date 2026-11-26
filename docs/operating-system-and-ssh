# Operating System and SSH Setup

## Current setup
- Raspberry Pi 5
- Raspberry Pi OS Lite
- Hostname: PI_HOSTNAME
- SSH administration from Windows
- The Pi's Linux username is distinct from the Windows account username.

The LAN address used during setup was PI_LAN_IP. This is environment-specific and must not be copied blindly into another installation.

## Example Windows OpenSSH client configuration

```sshconfig
Host PI_HOSTNAME
    HostName <PI_LAN_IP>
    User <PI_LINUX_USERNAME>
    KexAlgorithms curve25519-sha256
```

Connect with:

```powershell
ssh PI_HOSTNAME
```

The key exchange override was used during initial troubleshooting with this Pi and Windows OpenSSH client. Other versions may not require it.

Verify SSH:

```bash
sudo systemctl status ssh --no-pager
```
