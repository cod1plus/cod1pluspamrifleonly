# cod1plus PAM - rifle only

The PAM run by the vcod.gg rifle match servers: **kvcodPAM** REV19 (by kikiii & Maggot,
ezya-cod2) with the **rPAM kvcodPAMext** v29 REV20net extension (by reissue_), plus the
rifle-match changes below. All the changes are in `rPAM_kvcodPAMext/`; `kvcodPAM_nolib_v2/` is
the official REV19, unchanged.

## Changes

- Rifle mode (`pam_mode ..._rifle`) no longer crashes the server (`enfield_scope_mp` is a United
  Offensive weapon, not a CoD1 one).
- `scr_rifle_teamweapon 1`: every player gets the Mosin-Nagant and the Kar98k (own side's rifle
  first), no pistol; the weapon menu shows the side's rifle only; no weapon and no mounted MG
  left in the maps.
- `scr_rifle_osok 1`: one shot one kill (bullet or rifle butt of an enemy).
- `scr_friendlyfire_override 0`: friendly fire value that replaces the rules' one.
- `scr_showhit 1`: hit marker.
- Search & Destroy fix: a bombzone touched during the strat time could not be planted for the
  rest of the round (mp_stalingrad A, where defenders can spawn inside it).

## Install

Copy the two pk3s of `pk3/` into the server's `__rPAMv115b5/` folder, in place of
`zzzzz_rPAM_kvcodPAMext_v29_REV20net.pk3` (keep the rest of the PAM pk3 set, map packs
included, from [cod1plus/cod1pluspam](https://github.com/cod1plus/cod1pluspam)). Server config:

```
seta pam_mode "comp_20rounds_rifle"     // or comp_mr12_rifle
seta scr_rifle_teamweapon "1"
seta scr_rifle_osok "1"
seta scr_friendlyfire_override "0"
seta scr_showhit "1"
```

## Build

```sh
python3 build.py                 # -> dist/*.pk3, names from VERSION
python3 build.py --verify pk3    # compare with the pk3s of pk3/, file by file
```

Bump `EXT_REV` in `VERSION` for every change: sv_pure clients keep a pk3 of the same name and
never download it again.
