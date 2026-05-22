# MATTMACHINE TASKS

## Current QA pass

Tested from repository source and main app wiring.

## Immediate click-test findings

- WAKE button is wired to create/resume AudioContext.
- IMPORT input is wired and can auto-slice imported audio into the selected bank.
- RELOAD button is wired to sample manifest autoload.
- STOP button is wired to stop one-shots and loops.
- AUTO SLICE toggle is wired.
- CHOKE toggle is wired.
- CLEAR BANK is wired.
- CLEAR PAD is wired.
- Keyboard triggers are wired for 16 pads.
- Per-pad REC buttons are wired to mic recording.

## Found issues

1. Pad buttons contain nested REC buttons. This is invalid HTML and can cause touch/click problems on mobile.
2. README is outdated: it describes 8 pads, long-press recording, volume/pitch controls, and next-phase sample packs, while the app currently has 16 pads, REC buttons, no visible pitch/volume controls, and sample manifest loading already present.
3. Quantized loop launching is not implemented yet. Current loops start immediately.
4. Hold behavior currently acts like momentary loop hold, not a latched/toggle loop.
5. Sample manifest files load from `samples/`, `samples/packs/`, `packs/`, or root, but the folder list in the manifest is not used for lookup.
6. The live app should be browser-tested on mobile after the nested-button fix.

## Next fixes

- Replace pad `<button>` wrapper with a non-button interactive container so REC buttons are valid and reliable.
- Update README to match the current build.
- Add true quantize scheduling.
- Add optional loop latch mode.
- Add visible test panel/status readout for button events.
- Add mobile tap-stress testing notes.

## Framework direction

MATTMACHINE is the shared core/framework.
MBK should become a lightweight mobile/performance interface using the MATTMACHINE core instead of duplicating audio engine work.
