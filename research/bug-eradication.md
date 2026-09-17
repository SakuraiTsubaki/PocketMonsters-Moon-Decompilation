# Bug / Glitch Eradication Track — Pocket Monsters Moon

## Objective

Remove every reproducible bug, glitch, crash, softlock, incorrect battle rule, text/data error, visual/audio defect, overflow/underflow, invalid state transition, save-risk condition, and other unintended behavior that can be demonstrated in the selected Pocket Monsters Moon target.

This file is an evidence-backed starting inventory, not a claim that the list is already exhaustive. New findings must be added rather than silently omitted.

## Target state

- Repository target: Pocket Monsters Moon
- Platform: Nintendo 3DS
- Latest official game update baseline: Ver. 1.2
- Exact ROM/update/region/revision/hash in this repository: **not selected yet** (`config/target.json`)
- ROM binaries remain outside Git; hashes, extracted non-ROM data, patches, tests, logs, and reports belong in the repository.

## Required workflow

1. Identify the exact base ROM and update-layer hashes.
2. Produce deterministic ExeFS/RomFS/code/data inventories.
3. Reproduce every known issue on the selected build when applicable.
4. Locate the responsible code/data/script/resource path.
5. Implement the smallest behavior-correct fix without deleting unrelated original content.
6. Add a regression test or reproducible verification case.
7. Verify normal play, save compatibility, version-exclusive behavior, and adjacent systems.
8. Record fixed / not-applicable / cannot-reproduce / needs-more-evidence status with evidence.

## Officially fixed issues that must remain fixed

### Ver. 1.1

- Memento / Parting Shot malfunction, including Z-Move related online failure.
- Rocky Helmet final-Pokémon win/loss determination.
- Some evolution-time move-learning failures.
- Other official gameplay adjustments.

### Ver. 1.2

- Sky Drop interaction with Spiky Shield.
- Scatterbug Egg Move learning.
- Poké Pelago end-of-month completion bug (reported with the 1.2 fix set).
- Rare crash when the final copy of an Evolution item is used (reported with the 1.2 fix set).
- Other official gameplay fixes.

## Known latest-version candidates to investigate and eliminate

### Battle / mechanics

- Charge Beam additional-effect chance overflow with Serene Grace + pledge rainbow.
- Rollout stored-power state surviving interaction with Mimikyu Disguise.
- Shell Trap + Encore stale trap state.
- Toxic same-turn sure-hit state leakage.
- Trick Room effective-Speed overflow/rollover at extreme Speed values.
- Baton Pass + Own Tempo delayed confusion cure.
- Choice-item lock state surviving item removal/negation.
- Confusion self-damage failing to trigger threshold items immediately.
- Protean + Curse incorrect target/behavior transition.
- Sparkling Aria-based ally AI selecting an invalid damaging Z-Move target in the Hau Multi Battle case.
- Sky Drop target becoming invisible when the user faints/switches as damage resolves with battle effects disabled.
- Terrain/weather background state desynchronization.
- Transformed Ash-Greninja Water Shuriken rendering state corruption on hit 4/5.
- Z-Move background-music attenuation state occasionally failing after a same-turn faint in Double Battles.

### Data / text / legality

- Case-conversion failure for language-specific characters in text entry.
- Japanese/Chinese emoticon display mapping error.
- Giratina + Nectar invalid form/cry behavior.
- Therian Thundurus incorrectly blocked from learning Smart Strike.
- Battle Team four-digit number formatting error.
- GTS deposited-Pokémon model morphing to the previously viewed model.
- Known legality-check false positives for otherwise legitimate Pokémon combinations.
- TM bag text not reflecting that the current Pokémon already knows the move.

### Rendering / audio / presentation

- Alolan Exeggutor trade model fragment appearing briefly in the lower-left.
- Evolution model appearing for a frame before the evolution sequence.
- Pokémon Refresh using the default-form cry for the first cry of alternate forms.
- **Moon-specific:** Totem Alolan Raticate intro plays Gumshoos's cry.
- Totem Kommo-o outline disappearing from certain camera angles.
- Aether Paradise crate occlusion/outline artifact.
- Poni Wilds Berry-tree shadow flicker.
- Reported T-pose / stretched-model graphical corruption: reproduce and determine whether software, asset, hardware, or corrupted-data dependent before changing code.
- Vast Poni Canyon trial-site menu muting background music.
- NPC position reset immediately after some Egg hatches in Ver. 1.2.

## Evidence status rules

- `CONFIRMED-ROM`: reproduced against the selected ROM/update hash.
- `CONFIRMED-DATA`: directly proven by extracted code/data but not yet reproduced in gameplay.
- `OFFICIAL-FIX`: documented by Nintendo / Pokémon official update notes.
- `PUBLIC-REPORT`: reproducible public report not yet confirmed against our target.
- `RESEARCH-NEEDED`: trigger/cause/version scope remains uncertain.
- `FIXED`: patch applied and regression verification passed.

## Primary references

- Nintendo Support — Pokémon Sun / Moon update history: https://en-americas-support.nintendo.com/app/answers/detail/a_id/25400
- Nintendo Japan — Sun / Moon Ver. 1.2 update notes: https://support.nintendo.com/jp/3ds/soft/bnda/update/index.html
- Bulbapedia — Generation VII glitch index: https://bulbapedia.bulbagarden.net/wiki/List_of_glitches_in_Generation_VII
- Bulbapedia — Generation VII battle glitches: https://bulbapedia.bulbagarden.net/wiki/List_of_battle_glitches_in_Generation_VII
- Bulbapedia — Generation VII overworld glitches: https://bulbapedia.bulbagarden.net/wiki/List_of_overworld_glitches_in_Generation_VII

## Immediate blocker

No exact Moon ROM/update build is selected in `config/target.json`. Do not invent addresses, file names, symbols, offsets, or patch bytes. The next ROM-backed step is to fingerprint the actual input and turn the candidates above into reproducible test cases.
