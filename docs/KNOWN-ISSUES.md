# Known issues and test coverage

## Open issues

| Area | Current limitation |
|---|---|
| Remote animation/model | Characters can slide or show incorrect walking/model behavior. Unpublished 0.3 work is not included. |
| Save/menu flow | A freeze after saving and returning to the main menu was reported. Lock/input fixes exist; the full save → menu → Continue regression is pending. |
| Story and puzzles | Selected doors and use/one-shot touch triggers are shared; not every quest or puzzle variable is covered. |
| Enemy combat | Ownership/retargeting rules passed protocol tests. Native attack, damage and grab transfer need live validation. |
| Four-player play | Four UDP participants passed protocol tests. Four actual game instances have not completed a campaign regression. |
| Travel and cinematics | Not all chapter changes, cinematics, death and rejoin paths have been tested. |
| Steam builds | The owner reports Steam play working; the exact tested build/hash is unrecorded. The installer's single-fingerprint check can reject other builds. |
| UI language | English installer/launcher available; the current in-game co-op panel still uses Turkish labels. |
| Network | Radmin/LAN only; no built-in cloud server, Cloudflare connection or host migration. |

## Evidence available

- The project owner reported successful two-player play on the previous 0.2 build, and subsequently reported that Steam works.
- Four local UDP peers, capacity/room rejection, malformed packets and stale-peer timeout tests passed.
- Shared action delivery/acknowledgement, duplicate rejection and enemy ownership rules passed protocol tests.
- Separate-save persistence across process restart and corrupted-save rejection passed.
- An earlier live test observed hosting load `StartGame` and write a separate co-op save.
- Installer/distribution checks are recorded in [release validation](RELEASE-VALIDATION.md).

User reports, protocol tests, package tests and direct live-game observations are different kinds of evidence. None establishes full campaign compatibility by itself. Epic/Steam cross-store sessions have not been independently recorded as a separate test.
