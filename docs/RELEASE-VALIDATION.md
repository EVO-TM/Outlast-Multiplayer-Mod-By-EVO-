# 0.2.1 release validation

Date: 2026-10-31. These checks cover installation and distribution, not a complete new gameplay regression.

| Check | Result |
|---|---|
| Installer payload extraction | Passed; runtime and documentation only |
| Source files, debug symbols, user saves/logs in payload | Not present |
| Gameplay module | Byte-identical to the earlier 0.2 DLL |
| Install into a disposable folder using the supported real executable | Passed |
| Preserve existing room settings on reinstall | Passed |
| Refuse to overwrite an unrelated mod DLL | Passed |
| Back up a recognized previous DLL before update | Passed |
| Uninstall while preserving an unrelated file | Passed |
| Reject an unrecognized game executable | Passed |
| EVO-TM / 0.2.1.0 file metadata | Checked; metadata is not a certified digital signature |
| Installer interface | Opened and visually inspected |
| Download integrity | Uploaded installer downloaded again and checked against local SHA-256 |

The English installer is a language variant of 0.2.1. It preserves the same gameplay DLL and executable allowlist. Its extraction, native-DLL identity, install/reinstall, foreign-DLL rejection, update backup, uninstall, executable rejection, metadata and checksum checks passed before upload. The English UI was opened and visually checked. The original Turkish installer remains unchanged.

Gameplay DLL SHA-256:

```text
B409FCB80EB6B1FA10953986AE65EFE1E37DD890B2DCD4CF7D66E7A55D0B2ECC
```

The project owner reports successful two-player play and Steam compatibility. The exact Steam build/hash and a distinct cross-store test are not recorded. No new four-game/full-campaign test is claimed for this packaging/localization release. Animation/model fixes and the full save/menu/Continue regression remain outstanding.
