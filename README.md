# Anime Regex for Sonarr.

## Dual-Audio Regex
Having tested most of these settings, they work pretty well but Anime is a fickle beast to toy with so be warned. 

| Term | Score | Notes |
| :-- | :-- | :-- |
| `/(dual.audio\|dual-audio\|dual audio)/i`                                 | 250 | Dual-Audio |
| `/(\[Kametsu\]\|\[DHD\]\|\[LostYears\])/i`                                | 200 | Dual-Audio |
| `/(\[BluDragon\]\|\[Exiled-Destiny\]\|\[Cleo\])/i`                        | 190 | Dual-Audio |
| `/(\[GHOST\]\|\[xPearse\]\|\[MK\]\|\[Moodkiller\])/i`                     | 180 | Dual-Audio \| xPearse has some raws. |
| `/(\[NPC\]\|\[A-L\])/i`                                                   | 170 | Dual-Audio \| NPC is mostly older. |
| `/(\[Erai-raws\])/i`                                                      | 160 | Subs with multi such as German, French , Spanish, Italian, Russian, Arabic, Portuguese and English |
| `/(\[Asenshi\]\|\[AkihitoSubs\])/i`                                       | 150 | FanSubs|
| `/(\[HorribleSubs\]\|horriblesubs\|Sallysubs)/i`                          | 140 | Subs |
| `/(\[AnimeRG\]\|\[Judas\]\|Commie\|GJM)/i`                                | 130 | Anime RG has Dual Audio and multiple audio such as German, French, Italian, Spanish, Arabic, Portuguese. \| Similar to Erai-raws with multi subs. \| Subs |
| `/(\[SNSbu\]\|\[DB\]\|\[Coalgirls\]\|FFF\|FFFansubs\|BluRayDesuYo)/i`     | 120 | Subs, FanSubs|
| `/(\[CH\])/i`                                                             | 110 | Little bit of Dual-Audio \| Mainly Fansub |
| `/(\[Licca\])/i`                                                          | 100 | FanSubs |
| `/(\[Soldado\])/i`                                                        | 90  | FanSubs |
| `/(\[SakuraCircle\])/i`                                                   | 80  | Subs |
| `/(\[Orphan\])/i`                                                         | 70  | FanSubs |
| `/(\[Yabai\])/i`                                                          | 60  | FanSubs |
| `/(\[kBaraka\])/i`                                                        | 50  | Subs |
| `/(\[DeadFish\])/i`                                                       | 40  | Take 10bit fan-subbed videos from other groups and release an 8bit hardsubbed version of it. We do this because while 10bit offers quite a few advantages, not everyone's PS3, 360, hardware player, toaster etc can play it. |
| `/(\[NewbSubs\])/i`                                                       | 30  | FanSubs |
| `/(\[NoGrp\])/i`                                                          | 20  | FanSubs |
| `/(\[Nii-sama\])/i`                                                       | 10  | FanSubs |

### Must Not Contain List
```dub,
FuniDub,
[Golumpa],
[KaiDubs],
[PuyaSubs!],
[English Dub],
[Beatrice-Raws],
