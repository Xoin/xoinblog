---
layout: post
title:  "Secret and items"
excerpt_separator: <!--more-->
author: xoin
---

Asterix has 26 secret levels, in the first level two can be found easily by breaking a block and then grabbing the key. The first secret level can be found at `0x1C000`. At `0x3F31` the games items are stored.

<!--more-->

# Fun stuff

## Secrets

```
1:C000h: 6E 00 40 01 00 01 FF AA 55 00 02 03 04 05 06 07  n.@.....U....... 
1:C010h: 08 09 0A 0B 0C 0D 0E 0F 06 05 09 03 01 05 03 01  ................ 
1:C020h: 09 03 01 05 03 01 09 03 01 05 03 01 09 03 01 05  ................ 
1:C030h: 03 01 05 03 01 00 00 00 01 05 03 01 05 03 01 00  ................ 
1:C040h: 00 00 01 05 03 01 09 03 01 05 03 01 09 03 01 05  ................ 
1:C050h: 03 01 09 03 01 0F 03 01 0F 03 01 0F 03 01 0F 03  ................ 
1:C060h: 01 0B 03 01 00 00 00 0D 05 00 00 00 01 0B 03 01  ................ 
1:C070h: 00 00 00 01 0F 03 01 0F 03 01 09 03 01 05 03 01  ................ 
1:C080h: 09 03 01 05 03 01                                ......
```

The first byte indicates how much data it will have. These are unsinged, in the case of 6E this is 110 bytes. The ``00 40 01 00 01 FF AA 55 00 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F`` is the same for this type of level. The levels are drawn from the top left to the bottom left and then moved one tile to the right till the level is filled. This is different compared to normal levels. What it has incommon with normal levels is that tiles can be repeated. Repeating is done by have one byte indicate how often and then another for the tile ID. But just like normal levels just one byte for something is fine, just make sure everything adds up at the end.

If you grab the import stuff and create new lines every 16 bytes you can acuretlly dump or write levels
![image]({{ site.url }}/images/secrets.png)

## Items

So how are items stored? Well at `0x3F31` the first levels items are stored (including enemies!)
```
3F31h: 00 00 00 00 00 28 00 4F 01 36 80 00 3F 02 36 80  .....(.O.6..?.6. 
3F41h: 00 2F 03 36 C0 10 4F 04 01 30 01 67 05 0D F0 01  ./.6..O..0.g.... 
3F51h: 10 06 36 F8 01 10 07 36 F8 11 5F 08 03 10 02 2F  ..6....6.._..../ 
3F61h: 09 3B 68 02 2F 0A 34 78 02 77 0B 0A B0 02 57 0C  .;h./.4x.w....W. 
3F71h: 08 40 23 5F 0D 07 C4 03 2F 0E 37 DC 03 5F 0F 07  .@#_..../.7.._.. 
3F81h: 08 04 1F 10 3C 18 14 2F 11 04 20 14 77 12 09 A8  ....<../.. .w... 
3F91h: 14 17 13 04 D8 04 57 14 02 08 05 27 15 35 58 05  ......W....'.5X. 
3FA1h: 1F 16 36 70 05 1F 17 36 80 05 57 18 02 B0 05 27  ..6p...6..W....' 
3FB1h: 19 33 00 06 27 1A 36 08 06 27 1B 36 30 06 57 1C  .3..'.6..'.60.W. 
3FC1h: 10 18 07 27 1D 36 30 07 5F 1E 02 50 07 0F 1F 35  ...'.60._..P...5 
3FD1h: B8 17 77 20 07 A0 08 47 21 0A 00 19 27 22 04 10  ..w ...G!...'".. 
3FE1h: 09 2F 23 36 50 09 1F 24 36 EE 0E FF 25 3D FF 7F  ./#6P..$6...%=. 
3FF1h: 00 7F 7F 00 00 00 26 00 10 00 47 27 36 10 00 5F  ....&...G'6.._ 
4001h: 28 36 10 00 77 29 36 20 00 47 2A 36 20 00 77 2B  (6..w)6 .G*6 .w+ 
4011h: 36 30 00 1F 2C 36 30 00 47 2D 36 30 00 77 2E 36  60..,60.G-60.w.6 
4021h: 3C 00 1F 2F 36 40 00 77 30 36 48 00 1F 31 36 50  <../6@.w06H..16P 
4031h: 00 77 32 36 54 00 1F 33 36 60 00 1F 34 36 60 00  .w26T..36`..46`. 
4041h: 3F 35 36 60 00 57 36 36 90 00 17 37 3A FF 7F 00  ?56`.W66...7:.. 
4051h: 7F 7F 00 00 00 38 00 01 00 37 39 3A 10 00 4F 3A  ...8...79:..O: 
4061h: 36 20 00 17 3B 36 20 00 27 3C 36 28 00 57 3D 36  6 ..;6 .'<6(.W=6 
4071h: 38 00 1F 3E 36 38 00 2F 3F 36 40 00 5F 40 36 50  8..>68./?6@._@6P 
4081h: 00 27 41 36 50 00 37 42 36 58 00 67 43 36 68 00  .'A6P.7B6X.gC6h. 
4091h: 2F 44 36 68 00 3F 45 36 70 00 6F 46 36 88 00 17  /D6h.?E6p.oF6... 
40A1h: 47 33 90 00 6F 48 36 FF 7F 00 FF FF 00 00 00 C8  G3..oH6........ 
40B1h: 00 A0 00 7F C9 46 D0 00 7F CA 46 00 01 7F CB 46  ....F...F...F 
40C1h: 30 01 7F CC 46 FF 7F 00 FF FF                    0..F....
```

So the level starts with ``00 00 00 00 00`` followed by 5 bytes items:

```c
struct ITEM {
    short x;
    char y;
    char ?;
    char id;
} item;
```

it gets stopped at `FF 7F 00 7F 7F` followed by a `00 00 00 26 00` the 26 seems to be some unique byte it then does the secret level items till it hits `FF 7F 00 7F 7F`. Only in two cases it hits `FF 7F 00 FF FF` and then again does secret level items. For every other level it seems to end with as it gets followed with ``00 00 00 00 00``