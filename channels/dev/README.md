# DEV channel

**Active. Test systems only, not for customers.**

- **Signing key:** `7e9b0e6ac782de72261db275035c89c3f5a78324aab60ca587db0ab938df7979` (public key in `../../keys/trusted-keys.json`).
- **Releases:** GitHub pre-releases tagged `vX.Y.Z-dev`, created as drafts and published by the owner.
- **Servers read** the signed manifest attached to the release `channel-dev` (asset `manifest.signed.json`). Its
  sequence number only ever increases.
