# Monster Hunter Portable 3rd HD – Merged Texture Pack (NPJB40001)

One coherent HD texture pack for **Monster Hunter Portable 3rd HD ver.** (`NPJB40001`), built by merging
several community packs. It is made for the [Yakumo](https://gbatemp.net/threads/monster-hunter-portable-3rd-gets-a-static-recompilation-port-for-windows-linux-mac-and-android.684734/)
port, and it uses the standard PPSSPP texture-replacement format, so it also works in PPSSPP.

**This repository contains no original work.** Every texture belongs to the authors credited below,
and the game assets belong to Capcom. This repo only selects and merges their work into a single folder.

## Install

- **Yakumo**: put this folder at `data/textures/NPJB40001`, next to `Yakumo.exe` (portable mode), and
  enable texture packs in the settings.
- **PPSSPP**: put this folder at `PSP/TEXTURES/NPJB40001` and enable *Replace textures*.
- For the UMD version (`ULJM05800`), rename the folder.

## How the merge works

The **HolographicWings pack is the master**. Other packs only fill what the master does not have,
except the MHGU textures, which take precedence over everything. Sources are applied in priority
order, and for each texture hash (clut + data, with
`ignoreAddress = true`) the first source that really ships the file is used:

| Priority | Source | Folder in this pack |
|---|---|---|
| 1 | Pixel Cover – *MHGU HD Pixel Pack 4.0* (Monster Hunter Generations Ultimate, 2025-05) | `mhgu/` |
| 2 | HolographicWings – *Monster Hunter Portable 3rd HD Pack Enhanced* (commit `9e509a1`, v1.2.0+, 2026-10-24) | root (`equipment/`, `characters/`, `maps/`, `ui/`, …) |
| 3 | Ellym57f – *MHP3rd HD Definitive Edition* (commit `8e334a7`, 2023-01-11) | `definitive/` |
| 4 | StormieVN – *MHP3rd HD Remake* (commit `ca52133`, 2021-11-12, full-res version) | `stormie/` |
| 5 | Ngeradak Gaming – MHP3rd HD texture packs (YouTube, 2020-09 → 2021-06) | `ngeradak/` |

- Within the Ngeradak packs, the newest pack wins when two packs conflict.
- MHGU reuses many P3rd low-rank hunter armor, hunter weapon and Felyne textures. The `mhgu/`
  textures were matched by content to the P3rd originals (dumped from the game). They keep
  the colors of the HD Pixel Pack and the transparency of the P3rd original. Where MHGU leaves a part
  grey (tinted at runtime in MHGU), the colors of the P3rd original were put back.
- Where the master also has a texture, the MHGU one replaces it (`# [mhgu] overrides master`).
- A master entry whose file is missing upstream is filled by a lower source when one has it. These
  lines carry the comment `# [<source>] file missing upstream`.
- Entries are rewritten with comments when the master has the file under its hash name instead of
  the expected path (`# [auto-fix]`).
- Everything below the `# ===== SUPPLEMENTS MERGE =====` marker of `textures.ini` is generated.

### Files

- `textures.ini`: the active ini. Every entry points to a file that exists, or is an intentional
  "ignore" entry of the master.
- `textures_missing.ini`: entries whose texture file exists in **no** source. It is not loaded, and is
  kept for reference and as a to-do list. Contributions welcome.
- `textures.ini.upstream`: the untouched HolographicWings ini the merge starts from.

## Sources and credits

- **Capcom**: *Monster Hunter Portable 3rd* and all original art.
- **[HolographicWings/Monster-Hunter-Portable-3rd-HD-Pack-Enhanced](https://github.com/HolographicWings/Monster-Hunter-Portable-3rd-HD-Pack-Enhanced)**:
  fixes, remapping, new textures and optimization by HolographicWings. It is built on:
  - the original HD pack **[AFOOT03939/Monster-Hunter-Portable-3rd-HD-pack](https://github.com/AFOOT03939/Monster-Hunter-Portable-3rd-HD-pack)**
    by AFOOT, Darix, !-0 Kuña'i Ñakurutû (Tano), Effy and Stormie;
  - the **[David-vz/MonsterHunterPortable3rdHDRemake](https://github.com/David-vz/MonsterHunterPortable3rdHDRemake)**
    project;
  - a few textures from **[three5media's MHFU HD retexture](https://github.com/three5media/mfhu-hd-retexture)**.
- **[Ellym57f/Monster-Hunter-Portable-3rd-HD-Definitive-Edition](https://github.com/Ellym57f/Monster-Hunter-Portable-3rd-HD-Definitive-Edition)**:
  fork of the AFOOT pack. Credits: AFOOT, Darix, Tano, Effy and Stormie.
- **[StormieVN/MonsterHunterPortable3rdHDRemake](https://github.com/StormieVN/MonsterHunterPortable3rdHDRemake)**:
  Stormie's fork of the David-vz project (MHW icons, upscaled armor sets and weapons, fixes).
  Its optional variants (Xbox layout, MHW sharpness bar…) are not included.
- **Ngeradak Gaming** ([YouTube channel](https://www.youtube.com/channel/UCjyhPL4rLDJYJG-o5lZfVKw)): HD
  weapon and armor textures, including many female armor sets. The packs used are:
  - All Weapon (GS, LS, SnS, DB, SA, H, HH, L, GL, LBG, HBG, B)
  - Armor & Weapon 1, 2 and (F) 1–3, Weapon 1
  - Armor 1 and 2
  - Spesial Deviljho, Spesial Diablos, Volcano and Special Alatreon
  - the Jaggi and Aelucanth side packs, and the Monsters pack
- **Pixel Cover** ([YouTube](https://www.youtube.com/channel/UCmVt_09lfzye3AjKd9E6pUg),
  [HD Pixel Pack v4 video](https://www.youtube.com/watch?v=iacY54dZF8k)): *MHGU HD Pixel Pack 4.0* for
  Monster Hunter Generations Ultimate. 76 HD low-rank textures come from it: 35 hunter armor pieces
  (mostly female sets), 15 hunter weapons and 26 Felyne armor and weapon pieces.

If you are one of the authors and want your work credited differently or removed, please open an issue.
