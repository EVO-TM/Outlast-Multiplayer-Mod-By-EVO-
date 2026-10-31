# How EVO Outlast Co-op works

This overview describes the released 0.2 gameplay module used by 0.2.1. It separates implemented systems from outstanding gameplay validation. The source implementation remains private.

## Session and player presence

One player's game hosts a UDP session for up to three guests. Each player runs their own Outlast installation. The host relays player snapshots, while each client creates remote character actors only for active peers on the same map.

Snapshots carry player identity/name, map and checkpoint, position, rotation, velocity and cinematic state. Remote avatars are moved toward incoming positions. They are display actors rather than additional locally possessed players; collision and physics are disabled on them. This distinction is one reason interaction and animation behavior still needs work.

The current release has room-code matching, protocol/packet-size checks, finite-coordinate checks, sequence handling and peer timeouts. These are connection/protocol controls, not a claim of an encrypted, authenticated public-server platform. Radmin/LAN is the released connection workflow.

## Starting and joining

Hosting from the main menu starts a new co-op game at the opening base-game checkpoint. Joining waits for a host response and explicitly loads the host's checkpoint. A co-op resume also restores the saved room settings and checkpoint.

Automatic ongoing checkpoint following is disabled by default. Joining/resuming is not continuous world-state streaming, and one player advancing does not promise that every other game has completed the same scripted sequence.

## Shared doors and story interactions

The mod captures supported door events and selected interaction roots. Door messages include the target opening ratio, state/break state and lock flag. Supported story roots include use interactions and touch triggers configured to run once.

The host orders supported actions, sends them with acknowledgement/retry handling, and rejects duplicate/replayed actions. Other clients resolve the matching world object and apply the supported event. This covers a defined subset of interactions; arbitrary quest scripts, all puzzle variables and every campaign trigger are not synchronized.

## Enemy ownership and nearest-player targeting

The host chooses the nearest eligible player to own an enemy's simulation. The owner runs the game's native enemy AI against their real local player. Other clients disable their duplicate controller tick and mirror the received enemy pose.

Ownership uses a small stability delay/distance margin to reduce constant switching, normally remains with the owner during an attack, and can be reassigned when an owner disconnects or stops updating. Map, player activity and cinematic state affect eligibility.

Nearest-player assignment and attack ownership rules passed protocol tests. Native attacks, damage, grabs and ownership changes during real multi-PC combat have not been comprehensively verified. This is not a guarantee that every enemy action works against every guest.

## Local cinematics

Cinematic playback belongs to each player's local game. Remote character actors are hidden when the local player enters cinematic mode, so extra co-op bodies are not intentionally inserted into that cinematic. All scripted/cutscene transitions have not been validated, and this is not a synchronized cinematic voting or skip system.

## Co-op saves

Co-op saves are separate from the ordinary single-player save. They contain the checkpoint, session settings and supported action history. A background worker writes through a temporary file, checks file integrity and replaces the save atomically, retaining a previous `.bak` copy.

Restoring a save reloads a checkpoint and replays supported state; it does not recreate every live actor, position or puzzle variable. A full save → menu → Continue regression is still required for the reported freeze.

## Performance work in the released baseline

- Cached event classification avoids repeated reflection work for unrelated warm engine events.
- World object scanning is incremental and skipped for a lone host.
- Player snapshots are rate-limited to approximately 30 per second, world processing to 20 Hz, and NPC transport to 10 Hz.
- Unchanged movement updates are skipped, and save writes run on a worker.
- Verbose developer dumps are disabled by default.

These are implementation limits, not minimum FPS or latency guarantees. The unpublished 0.3 animation/model/FPS experiments are not included in 0.2.1.

## What is outside this release

There is no dedicated headless game server, built-in cloud relay, Cloudflare transport, automatic host migration, full campaign-state replication or complete native animation synchronization. The cover artwork is promotional, not a gameplay verification image.
