# Tidebreaker Flight and Cyberware Companion

Two Crimson Desert ASI mods in development by Raebeees. Source snapshot for review and potential CDAL porting; not an installable release.

## Source

Download and extract `tidebreaker-cyberware-source.zip`. It contains both projects' C++ source, headers, tests, build scripts, MinHook with its licenses, and a source hash manifest.

- **Tidebreaker Flight R49:** custom flight, animation and VFX integration. The installed baseline is user-reported working without crashes. A crow effect remains after boost followed by a ground stop.
- **Cyberware Companion, November 6 snapshot:** selectable cyberware and equipment-linked behavior. The local build matches the installed plugin SHA-256: `fde45818b1a2d42a6a2e1bd4668bb027250cc86b6bfd13da88958caf26e67278`.

## Build and dependency limits

Windows x64, MSVC and the Windows SDK are required. Existing scripts target Visual Studio 18 Community; adjust that compiler path for your installation. Run scripts from the corresponding project directory. MinHook source and original licenses are included.

**Tidebreaker:** `tidebreaker/build.cmd` builds the ASI and runs trace, wait and isolated loader checks. Runtime use additionally requires the matching game build, Character Creator, Combat Evolved, DMM and mod asset package. Hash and instruction checks remain in the code. The older readiness test requires a separate local fixture at `fixtures/runtime-readiness.tsv`, which is not included.

**Cyberware:** `cyberware/build.cmd` also requires the project's Character Creator adapter sources under `cyberware/dependencies/CharacterCreator`, plus the matching `cyberware/resources/partprefabtable.pappt` registration table. These are not included. The public Character Creator source snapshot is 9.1.21, while the installed plugin target is 9.1.36; they are not the same source version. Upstream: https://github.com/Khione95/Crimson-Desert-Character-Creator. The locally modified adapter must be reviewed separately before a reproducible public build is possible.

Local machine paths in Cyberware were replaced with `C:/Modding/dmm/mods/Cyberware Plate Mesh Diagnostic`; configure both `contact_runtime.h` and `registration_guard.h` consistently. The desktop test uses a relative dependency path. Publication edits do not modify the installed mods.

This snapshot excludes game assets, registration-table payloads, compiled plugins, profiles, private logs and third-party Character Creator source. It is not a complete playable package. Do not remove runtime guards to force it to load.

## CDAL beta interest

Current integration uses build-specific addresses and checks. Tidebreaker uses MinHook detours and guarded function-table replacements. Shared IDs of interest include movement, animation, equipment, effects and cleanup. Neither project is ported to CDAL yet.

Development is AI-assisted, with in-game testing and feedback by the author. Existing test source is included; publication checks are not a new gameplay acceptance result.

## Licensing

MinHook retains its included license and notices. No new license is granted for the project code in this snapshot. Third-party mods and game assets remain subject to their respective terms.
