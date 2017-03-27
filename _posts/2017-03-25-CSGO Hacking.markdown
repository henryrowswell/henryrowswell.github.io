---
layout: post
title:  "CSGO Hacking"
date:   2017-03-26 03:09:00 -0700
categories:
description: "C# Trigger Bots and Wall Hacks"
---

I've always wondered how to hack / cheat video games. That's why I used to be into modding Minecraft (back in high school). This year, as I started playing CSGO more I got more and more curious about how people hack in this game. Hackers are pretty prevalent in CSGO, and I wondered if they were able to somehow decompile the code in order to modify it since that's how I used to modify Minecraft.

Anyway whenever I was curious I would do a quick Google search to see what I could find but the first couple times I wasn't able to really find anything (I guess my searches were bad). But then a few days ago, my curiosity peaked again and I stumbled upon exactly what I was looking for.


### TL;DR
You don't have to decompile anything, these hacks used a tool called Cheat Engine which is able to scan and modify the memory addresses that important game variables are stored at. I found a series of great tutorials that taught me how to create a Bunny Hop Hack, Trigger Bot, and Wall Hack. However, currently none of them are actually usable in online matches because Valve's Anti-Cheat (VAC) system can supposedly detect them really easily and ban your account immediately.
* [HazardEdit Tutorials](https://www.youtube.com/user/HazardEdit/)
* [My Code](https://github.com/henryrowswell/csgo_hacking)
* Launch Options: `-insecure +sv_lan 1`


### Cheat Engine & Offset Dumper

I was hesitant to download Cheat Engine because it sounds like the kind of thing that would come with complimentary malware to hack you instead of allowing you to hack anything. Who knows, maybe I do have malware now but I think Cheat Engine is really cool.

It allows you to modify the values stored in memory at a given address or pointer, and can also scan memory for certain values if you don't know the address. For example, say you want to give yourself unlimited health. If your health starts at 100, you could search memory for addresses with the value 100. But there are a lot, so next you decrement your health in game, to 95. Now you search for 95, and Cheat Engine can narrow down your search to values that used to be 100 and are now 95. This is tedious and there are better ways, but after a few scans you'll be able to find where your health is stores in memory. In simple single player games, you could just modify the value in memory at that address, and your health would change in game!

This is cool, but also a huge pain because every time you start the game it will be in a different place in memory. To get around this, in CSGO there are known "offsets" where variables are always stored. These offsets only change sometimes between game updates, and they are simply an offset from the game's base address. For example, we know the local player data is stored at offset `0x00AB06EC`, which means in Cheat Engine we go to `"client.dll" + 0x00AB06EC`. It works similar to a pointer. These offsets can be found online but are often out of date, so I also found a tool called Offset Dumper which will find them for you. Offset Dumper is just a command line program that needs to run while CSGO is running, and it magically finds and outputs all the offsets to a text file.

![Cheat Engine]({{site.url}}/assets/cheat_engine.png){:class="img-half"}
![Offsets]({{site.url}}/assets/offsets.png){:class="img-half"}

### Bunny Hop

To be honest, I don't fully understand the point of this hack, but I do understand the code. There is a specific variable stored in memory that CSGO uses to indicate whether the player is on the ground or not. This hack simply checks if we are on the ground, and if the space bar key is held down it will write to memory to trigger the player to jump.

The part I don't get is you could accomplish the same thing by binding jump to a "spam-able" button like the mouse-wheel. All it does is allow you to continuously jump, but my understanding is that in order to bunny hop you need to combine this with strafing left and right, which allows you to move at a higher speed than normal running. And THAT is the hard part!

### Trigger Bot

CSGO actually stores a variable that checks if there is a player in the crosshair, which they probably use to detect bullet collision, but is also super useful for us. This hack simply checks if there is a player in the crosshair and it's on the enemy team and its health > 0, then shoot.

### Wall Hacks

This one is also surprisingly easy, because the functionality already exists within the game. In spectator mode, you are able to see outlines of all players, even through walls. This hack simply loops through all players and activates the glow property. It's just a little tedious because each player's glow has a red, green, blue and alpha value, as well as rwo and rwuo which I think are the boolean values to activate glow.

![Wall Hack]({{site.url}}/assets/wallhack.jpg){:class="img-half"}

### Valve Anti-Cheat (VAC)

This is something I'd definitely like to learn more about, but I've gotten a glimpse into how it works. VAC is an automated system that checks if you do anything you shouldn't normally be able to do. For example, the player's view point angle is usually a value between -180° and 180°, so although 360° may be equivalent, if you set your view angle to a value above 180° you're busted because there's no way you could do that through normal game play. Another example I heard about is if your viewpoint suddenly changes to look directly at a special point like 0,0 (which is in the middle of the sky). It also supposedly monitors certain memory addresses (like traps), and if you modify them you're busted. So when I'm testing these hacks I have to be extra sure that I'm running in offline mode with bots and insecure mode (with the -insecure launch option) which is supposed to disable VAC.

### Next
* [AimBot](https://www.youtube.com/watch?v=NUeifQK7ukM&list=PL40815C2DCA521507&index=1)
* [Generalalized Game Hacking](https://www.youtube.com/watch?v=tntGFnPg1u8&list=PL2C03D3BB7FAF2EA0&index=2)
