# KH CoreGuard releases

This repository contains **only** KH CoreGuard release files and signed release manifests. It contains no source
code. KH CoreGuard Servers read the signed manifests from here to find updates.

## Products
- **KH CoreGuard Server + Web Admin Console**
- **KH CoreGuard Client** (agent, Enforcer, Client Updater)

Both are installed with one Windows setup.

## Channels
| Channel | Status | Release tags | Manifest read by Servers |
|---|---|---|---|
| DEV | active, **test systems only, not for customers** | `vX.Y.Z-dev` (pre-release) | `channel-dev/manifest.signed.json` |
| BETA | **inactive** (no signing key) | `vX.Y.Z-beta` (pre-release) | `channel-beta/manifest.signed.json` |
| STABLE | **inactive** (no signing key; needs code-signed files) | `vX.Y.Z` | `channel-stable/manifest.signed.json` |

There are no releases yet.

## How updates are verified
A file from this repository is trusted only if all of these hold:
- **Signature:** it is listed in a release manifest signed with a release key whose **public** part is built into
  KH CoreGuard (`keys/trusted-keys.json`, one key per channel).
- **Content:** its size and SHA-256 match that signed manifest.
- **Version:** the manifest is for the installation's own channel, newer than any manifest seen before (no rollback or
  replay), and not expired.

GitHub is only the transport. Private signing keys are never stored here or on GitHub.

## Unsigned code
DEV builds are **not code-signed** (no Authenticode certificate yet), so Windows SmartScreen / Smart App Control may
block them. They are never offered as customer releases. STABLE releases require code-signed files.

## Verify a download yourself
```
Get-FileHash .\KH-CoreGuard-Setup-<version>-dev.exe     # compare with SHA256SUMS of the release
khctl release verify -keys keys\trusted-keys.json -channel dev -in manifest.signed.json
```
