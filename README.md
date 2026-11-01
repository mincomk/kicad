# kicad

Personal KiCad library: symbols, footprints and 3D models for the parts used in my
boards. Collected from the vendor download bundles that live in
[`mincomk/flyer`](https://github.com/mincomk/flyer) under `kicad/`.

## Layout

```
.
├── symbols/      # one .kicad_sym per part (library nickname == file name)
├── footprints/   # one .pretty directory per part
└── models/       # .step 3D models exported by the vendor
```

Each library is named after the vendor part, not after the symbol inside it, so the
provenance stays obvious. Where a vendor ships several land-pattern variants
(`-L`, `-M` suffix), all of them are kept.

## Contents

| Library | Symbol(s) | Footprints | 3D model | Source |
|---|---|---|---|---|
| AP65400P | `AP64500SP-13` | `SO-8EP_DIO`, `SO-8EP_DIO-L`, `SO-8EP_DIO-M` | - | Ultra Librarian |
| BMP581 | `BMP581` | `QFN10_BMP581_BOS`, `-L`, `-M` | - | Ultra Librarian |
| DPS310 | `DPS310XTSA1` | `XDCR_DPS310XTSA1` | `DPS310XTSA1.step` | SnapMagic (SnapEDA) |
| HMC5883L-TR | `HMC5883L-TR` | `XDCR_HMC5883L-TR` | `HMC5883L-TR.step` | SnapMagic (SnapEDA) |
| ICM-45686 | `ICM-45686` | `IC_ICM-45686` | `ICM-45686.step` | SnapMagic (SnapEDA) |
| ICM42688P | `ICM-42688-P` | `LGA14_2P5X3X0P91_TDK`, `-L`, `-M` | - | Ultra Librarian |
| MMC5983MA | `MMC5983MA` | `MMC5983MA_MEM` | - | Ultra Librarian |
| MP2760GVT-0000-P | `MP2760GVT-0000-P` | `TQFN-30_MP2760_MNP` | - | Ultra Librarian |
| SAM-M10Q-00B | `SAM-M10Q-00B` | `XCVR_SAM-M10Q-00B` | `SAM-M10Q-00B.step` | SnapMagic (SnapEDA) |
| SX1280 | `SX1280IMLTRT` | `XCVR_SX1280IMLTRT` | `SX1280IMLTRT.step` | SnapMagic (SnapEDA) |

`AP65400P` is the folder the vendor bundle shipped in; the symbol inside is
`AP64500SP-13`.

The `.step` files are not referenced from the footprints (the vendor `.kicad_mod`
files carry no 3D model path). Attach them by hand in the footprint properties if you
want 3D previews.

## Using the libraries

KiCad resolves path variables in library tables, so define one variable once and
point the table at it.

1. Preferences -> Configure Paths: add `KICAD_LIB_ROOT` = the path of this checkout.
2. Merge the entries of [`sym-lib-table`](sym-lib-table) into
   `~/.config/kicad/<version>/sym-lib-table` and [`fp-lib-table`](fp-lib-table) into
   `fp-lib-table` in the same directory (keep the surrounding `(lib_table ...)` from
   the file that already exists and paste the `(lib ...)` lines in).

For a single project, paste the same `(lib ...)` lines into the project's own
`sym-lib-table` / `fp-lib-table` instead.

## Licensing

These files are vendor-supplied models, not my work, and they are under the vendor
terms rather than an open license. See [NOTICE.md](NOTICE.md) before reusing or
redistributing them.
