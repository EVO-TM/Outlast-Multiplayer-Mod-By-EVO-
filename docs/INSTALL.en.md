# Installation and co-op guide

## Download and install

1. Open the [0.2.1 release](https://github.com/EVO-TM/evo-outlast/releases/tag/v0.2.1).
2. Download **EVO-Outlast-Coop-Setup-0.2.1-English.exe**. The original Turkish installer remains available as **EVO-Outlast-Coop-Setup-0.2.1.exe**.
3. Close Outlast, run the installer and select the game's root directory. It must contain `Binaries` and `OLGame`.
4. Select **INSTALL / UPDATE**. An unrecognized executable stops installation before the mod is copied into the game.
5. Launch Outlast through your normal game launcher. Select **Co-op** in the main menu. During gameplay, press **F9**.

Support files are installed under `%LOCALAPPDATA%\EvoOutlast`. The gameplay DLL is placed at `Binaries\Win64\dinput8.dll` inside the game installation. The installer does not replace an unrecognized DLL belonging to another mod.

## Compatibility

The Epic Outlast 1.0.8767.0 x64 executable was checked locally. The project owner also reports that the mod works with Steam; the exact tested Steam build/hash has not been captured.

The current installer accepts this `OLGame.exe` SHA-256, regardless of storefront:

```text
06C1C37C7F1D0BD0296328FF977FF847BEE82F878FB4D79F4282A026AEF68A96
```

Steam installations normally live under a Steam library's `steamapps\common\Outlast` folder. Use **Browse** if your library is not detected. A different executable fingerprint can still be rejected; a report that Steam works does not establish compatibility with every Steam build.

For a rejected build, report the store, file version and executable SHA-256 in an issue. Do not upload the game executable. Outlast 2 and The Outlast Trials are not supported.

## Host a session

1. Everyone joins the same private Radmin VPN network.
2. Open the in-game Co-op panel and enter your player name and a room code of at least eight characters.
3. Select **Oda aç ve başlat** (**Host and start**). A new co-op game loads the opening checkpoint.
4. Give your friends your Radmin IPv4, room code and UDP port. The default is **27851**.

The host is a running player's game, not a dedicated remote server. Keep that game running for the session.

## Join a session

1. Install the same mod version and join the host's Radmin network.
2. Enter the host's **Radmin IPv4**, not your own address. `127.0.0.1` only connects to the same computer.
3. Match the host's room code and port.
4. Select **Katıl ve başlat** (**Join and start**). Once connected, the join flow loads the host's checkpoint.

For connection problems, compare the Radmin network, address, code and port first. If a firewall rule is needed, allow only the game's necessary traffic on the appropriate network. Do not disable the entire firewall. The installer does not alter firewall or network settings.

## In-game label reference

The English installer and launcher do not change the current gameplay DLL's Turkish co-op labels.

| In-game label | English meaning |
|---|---|
| Oda aç ve başlat | Host and start |
| Katıl ve başlat | Join and start |
| Bağlantıyı kes | Disconnect |
| Co-op kaydet | Save co-op |
| Co-op kaydından devam et | Resume co-op save |
| Adın | Your name |
| Oda kodu | Room code |
| Boş yer | Empty slot |

## Save and resume

Press **F9 → Co-op kaydet**. Saves are kept in:

```text
%LOCALAPPDATA%\EvoOutlast\CoopSaves
```

The file stores the checkpoint, room settings and supported shared action history. It does not capture every player/NPC position, puzzle variable or arbitrary world state. Supported progress changes also schedule an autosave.

To resume, the host opens their co-op save first; guests reconnect to the same host. Use **Continue** or **Co-op kaydından devam et**. A freeze after saving and returning to the menu has been reported; the full save/menu/Continue regression remains open. Back up `CoopSaves` before testing a long session.

## Update and remove

Close Outlast before updating. The installer preserves existing room settings and co-op saves. When replacing a recognized older mod DLL, it keeps a copy under `%LOCALAPPDATA%\EvoOutlast\Backups`.

To remove the mod, close Outlast, open `%LOCALAPPDATA%\EvoOutlast\EvoOutlast.exe`, and select **Remove mod** in the English launcher. The original Turkish launcher uses **Modu kaldır**. Co-op saves remain on disk.

## Verify the download

The release's `SHA256SUMS.txt` lists both installer variants. In PowerShell:

```powershell
Get-FileHash .\EVO-Outlast-Coop-Setup-0.2.1-English.exe -Algorithm SHA256
```

Compare the result with the matching filename in `SHA256SUMS.txt`. Neither installer is Authenticode-signed; a checksum is an integrity check, not a certified publisher signature.
