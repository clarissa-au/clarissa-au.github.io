---
layout: post
title:  "HKCERT CTF 2023 Writeups - ReZero"
date:   2023-11-10 21:00:00 +0800
category: 
    - ctf
    - hkcert23ctf
---

Here is the writeup for 從零開始的新世界!

> `hkcert23{he110_aga1n_4nd_we1c0m3_t0_hkc3r7_c7f}`

## 從零開始的新世界 (150 pts) (with guide)

The official guide is [here](https://hackmd.io/@blackb6a/hkcert-ctf-2023-i-zh-378c762700aa0175#ReZero--%E5%BE%9E%E9%9B%B6%E9%96%8B%E5%A7%8B%E7%9A%84%E6%96%B0%E4%B8%96%E7%95%8C-Web).

### Solution

1. I don't want to play the game!!!
2. Where the fuck is the data stored? I looked at storage -  
    data:"{"hasAlreadyPlayed":true,"player":{"name":"test","weapon":"sword2","armor":"clotharmor","image":"data:someBase64Txt"},"achievements":{"unlocked":[],"ratCount":0,"skeletonCount":0,"totalKills":0,"totalDmg":98,"totalRevives":1}}"
3. I need to have achievements from 0 - 20, as well as 0 totalKills, 0 totalDmg and 0 totalRevives.
4. Apparantly Firefox cannot do inclient storage modification, I downloaded a extension to edit the data into -
    data:"{"hasAlreadyPlayed":true,"player":{"name":"test","weapon":"sword2","armor":"clotharmor","image":"data:someBase64Txt"},"achievements":{"unlocked":[0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20],"ratCount":0,"skeletonCount":0,"totalKills":0,"totalDmg":0,"totalRevives":0}}"
5. Why still no flag after CTRL-R? Because I searched for "flag" not "hkcert"!
6. Filtering for "hkcert" gives the flag `hkcert23{m0dm0d__loc4l__stor4g3}`.
