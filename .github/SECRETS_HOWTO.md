# Secrets Quick Reference
# Run this to get the exact values needed for GitHub Actions secrets

```
KEYSTORE_PASSWORD: android
KEY_ALIAS: androiddebugkey
KEY_PASSWORD: android
```

To get KEYSTORE_BASE64, run on the machine with the keystore:
```bash
cd /root/cloudstream_gate/cloudstream
base64 -w0 _apk_rebuild_final/debug.keystore
```

Copy the output as the secret KEYSTORE_BASE64.

---

# Keystore Certificate Info (for verification)
```
Owner: CN=KA Play, OU=Mobile, O=Francisco Alro, L=Brasilia, ST=DF, C=BR
Issuer: CN=KA Play, OU=Mobile, O=Francisco Alro, L=Brasilia, ST=DF, C=BR
SHA256: DE:74:60:E7:98:38:42:C5:0A:7C:0C:BE:44:D4:55:14:76:75:A7:8A:CA:4B:B4:88:0C:7B:EE:28:21:A3:7F:EE
SHA1: EE:D5:84:59:D4:0B:93:58:A1:BF:88:D1:4A:56:8F:EB:03:0A:88:67
Valid: Oct 16, 2026 → Mar 3, 2054
```

This is the official KA Play release certificate.
