# Anime Regex for Sonarr.

## Dual-Audio Regex
Having tested most of these settings, they work pretty well but Anime is a fickle beast to toy with so be warned. 

---

## Media Management
There a few settings which make life a lot easier when tracking down and keeping certain information for your Anime. A lot of this is from [TRaSH](https://trash-guides.info/) with tweaks to make it work better with HamaAgent for plex.
| Name | Input | Notes |
| :-- | :-- | :-- |
| Anime Episode Format | `{Series TitleYear} - S{season:00}E{episode:00} - {absolute:000} - {Episode CleanTitle} [{Preferred Words }{Quality Full}]{[MediaInfo VideoDynamicRange]}[{MediaInfo VideoBitDepth}bit]{[MediaInfo VideoCodec]}{[Mediainfo AudioCodec}{ Mediainfo AudioChannels]}{[MediaInfo AudioLanguages]}{-Release Group}` | Has all necessary information and a little extra if you needed to rebuild. |
| Series Folder Format | `{Series TitleTheYear} [tvdb-{TvdbId}]` | ~~We do not want year here as it messes with the HamaAgent and how it identifies the anime. [Reference](https://forums.plex.tv/t/rel-http-anidb-metadata-agent-hama/40470/2043?u=visoseph)~~ I'm a dummy. Adding year back in with tvdb id allows matching to be correct. Thanks salty.  |
| Season Folder Format | `Season {season:00}` | Standard format that best covers most uses. |
| Multi-Episode Style | `Scene     S01E01-E02-E03` | 

### Example image of above
![Example image of above](images/MediaManage.png)

---

## Quality Profile
We need to set HDTV-1080p | HDTV-720p above WEB release as some groups have releases with incorrectly tagged media which causes issues when it thinks it is the best release.

![Image](images/QP.png)

---

### First Release Profile
| Term | Score | Notes |
| :-- | :-- | :-- |
| `/\b(uncensored)\b/i`                                                         | 1000 or -1000 | This is for if you want the uncensored version of anime. If you would like it to be priority then set to 1000. If you do not want uncensored set it to -1000.
| `/\b(dual)([ ._-]audio\b)\|EN\+JA\|JA\+EN/i`                                  | 500 | Dual-Audio profile. This and multi-audio are basically one and the same. But we still want dual-audio above multi. The EN+JA and JA+EN will only work if you follow my naming scheme above. |
| `/\b(dual)([ ._-]audio\b)/i`                                                  | 500 | * Only use this if you do not want to use the above
| `/\b(multi)([ ._-]audio\b)/i`                                                | 400 | Multi-Audio profile |

### Include Preferred when Renaming
We set this so when renames or new media is added it's easily identifiable as dual/multi audio.
![Image](images/FirstRP.png)

---

### Second Release Profile
| Term | Score | Notes |
| :-- | :-- | :-- |
| `/(ANThELIa\|\bZR\b\|kametsu\|\bctr\b\|\bscy\b\|deanzel\|\bshir\b)/i`     | 460 | Dual-Audio |
| `/(\bMK\b\|lostyears\|exiled-destiny\|E-D\|BluDragon\|Kawairemux)/i`      | 460 | Dual-Audio |
| `/(iahd\|anihls\|mkvultra\|\bdhd\b\|teneighty\|redblade\|haiku\|\bdhd\b\|walmart)/i` | 440 | Generic Dual-Audio
| `/(\[DragsterPS\])/i`                                                     | 420 | Multi-Audio - Multi-Subs (Usually from Netflix or similar) |
| `/(\[Koten_Gars\])/i`                                                     | 400 | Dual-Audio \| Mostly older content but has some newer stuff. Really good quality and searches different sources. |
| `/(\[Hark0n\])/i`                                                         | 380 | Dual-Audio \| Mostly older and limited, but what he does have is amazing quality.
| `/(\[GHOST\]\|\[xPearse\]\|\[Moodkiller\])/i`                             | 360 | Dual-Audio \| xPearse has some raws. |
| `/(\[NPC\]\|\[A-L\])/i`                                                   | 340 | Dual-Audio \| NPC is mostly older. |
| `/(\[Cleo\])/i`                                                           | 320 | Dual-Audio |
| `/(\[Erai-raws\])/i`                                                      | 300 | Subs with multi such as German, French , Spanish, Italian, Russian, Arabic, Portuguese and English |
| `/(\[Anime Time\]\|\[Mysteria\])/i`                                       | 280 | Subs mainly but has Dual-Audio |
| `/(\[Asenshi\]\|\[AkihitoSubs\]\|\[ASW\])/i`                              | 260 | FanSubs, occasional dual audio for ASW/Akihito |
| `/(\[SubsPlease\]\|\[Hi10\])/i`                                           | 240 | Subs, Replaces HorribleSubs below for newer content |
| `/(\[HorribleSubs\]\|horriblesubs\|Sallysubs)/i`                          | 220 | Subs (Now defunct but stil good SubsPlease has taken the mantle.) |
| `/(\[AnimeRG\]\|\[Judas\]\|Commie\|GJM)/i`                                | 200 | Anime RG has Dual Audio and multiple audio such as German, French, Italian, Spanish, Arabic, Portuguese. \| Judas: Similar to Erai-raws with multi subs. \| Subs |
| `/(\[SNSbu\]\|\[DB\]\|\[Coalgirls\]\|FFF\|FFFansubs\|BluRayDesuYo)/i`     | 180 | Subs, FanSubs |
| `/(\[CH\])/i`                                                             | 160 | Little bit of Dual-Audio \| Mainly Fansub |
| `/(\[Licca\]\|\[Soldado\])/i`                                             | 140 | FanSubs |
| `/(\[SakuraCircle\])/i`                                                   | 120 | Subs |
| `/(\[Orphan\]\|\[Yabai\])/i`                                              | 100 | FanSubs |
| `/(\[kBaraka\])/i`                                                        | 80 | Subs |
| `/(\[DeadFish\])/i`                                                       | 60 | Take 10bit fan-subbed videos from other groups and release an 8bit hardsubbed version of it. We do this because while 10bit offers quite a few advantages, not everyone's PS3, 360, hardware player, toaster etc can play it. |
| `/(\[NewbSubs\]\|\[Nii-sama\]\|\[Nii-sama\])/i`                           | 40 | FanSubs |

### Must Not Contain List (Added in with the second release profile)
The reason most of these are added is due to their shitty quality or just in general are not as good as other stuff that is out there. This can be tweaked as needed. Let me know if you run into any issues here. You should be able to just copy paste these in.

```
/(CuaP|EMBER|PnPSubs|ICEBLUE|URANiME|SLAX)/i,
/(Golumpa|KaiDubs|PuyaSubs|Beatrice-Raws|ohys-raws)/i,
/(?=(english|funi)).*(dub|dubbed)|\b(dub|dubbed)\b/i
```

### Image of above
We do not set preferred words here as it can cause issues with long filenames.

![Image](images/RP2.png)

---

### Acknowledgements
Most of my information and knowledge came from Kaiser#0101 and rg9400#7462 for the anime releases and best groups on discord and [TRaSH](https://trash-guides.info/) for his amazing regex.
