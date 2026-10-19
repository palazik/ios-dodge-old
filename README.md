# ios-dodge — iOS 16 (xnu-8796) kernel for OnePlus 13 (dodge / SM8750)

From-source XNU bring-up for the OnePlus 13 (Qualcomm SM8750 / Oryon), following
the proven method of **dipa-studio/ios-sweet** (iOS 16 on Qualcomm SM7150) — build
Apple's open-source XNU and add a non-Apple board config. Credit to dipa-studio
for the approach; all files here are our own (their repo has no license, nothing
was copied). XNU itself is Apple open source (APSL).

## What this builds
`xnu-8796.141.3` (macOS 13.5 / iOS 16 era) with a new **DODGE** board config:
plain arm64 (no PAC), `NO_MONITOR` (open in-kernel pmap), GICv3, 16K pages.
Built on GitHub macOS runners via blacktop/darwin-xnu-build.

## patches/
- `0001-dodge-add-OnePlus-13-SM8750-board-config.patch` — the board config
  (makedefs machine entry kept plain-arm64, board_config.h DODGE block, DODGE.h,
  config/MASTER.arm64.dodge with nos_arm_asm/nos_arm_pmap).
- More patches (build-enabling fixes, then drivers) land here as CI surfaces them.

## Build (CI)
`gh workflow run xnu.yml -R palazik/ios-dodge` (or the Actions tab). Artifacts:
`xnu-kernel` (the kernel Mach-O) and `xnu-buildtree` (to re-run single compiles).

See SETUP.md to activate the workflow (one step, due to a token-scope limit on
the automation that created this repo).
