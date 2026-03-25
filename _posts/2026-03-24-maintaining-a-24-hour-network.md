--- 
title: "How I Do Network Maintenance in a 24-Hour Casino"
date: 2026-03-24 
categories: [Network, Career] 
tags: [maintenance, upgrade, network] 
---

Most network administrators and engineers have maintenance windows, or at least times when people are out of office so they won't be impacted by network upgrades and changes. When I worked for an ISP, we'd head out at 1 AM to take an apartment building offline, because people were less likely to be using the network at that time.

At this point, though, I work at a 24-hour casino. There is no time of day that people aren't awake and actively using the network. There are *slower* times, sure, but no matter what, you're going to be impacting someone.

Right now, we're in the middle of a large-scale network refresh, where I'm replacing about a dozen access switches around the building. Here's the thing about access switches: there's no redundancy to the clients that are connected. If the switch goes down, the client goes down, and there's no way around it. However, in my time doing this, I've found a few tricks that definitely help me minimize the impact of the work that I do.

## 1. Indiana Jones

I'm not a big movie person. In fact, it's actually impressive to some people how many movies I *haven't* seen. One such movie is Indiana Jones (or, I guess, Raiders Of The Lost Ark), unless my dad had me watch it when I was much younger. Some may know where I'm going with this, others may be highly confused as to why I just brought up Indiana Jones in a post about network administration.

You know that scene in the movie where Jones swaps the idol on a pressure plate with a bag of sand as fast as he can, so the pressure plate can't detect that anything happened? Yeah, that's the tactic I try to implement when cutting over from one switch to another. Instead of taking all the cables out of one switch and connecting them to the other, I move them over one by one, with the jumper cable already connected to the new switch to make the swap so fast, you might only notice a little blip.

Similarly to the movie, this can backfire sometimes, specifically with PoE devices. If a workstation gets disconnected for a second (assuming the user isn't actively on a video call), the user may never notice that anything happened at all. What they will notice, though, is their phone rebooting on their desk. I do often check the phones that I'm disconnecting to ensure there isn't an active phone call going on, though. So far, this has worked without any complaints. I guess most users just go "huh, that was weird" and move on with their day.

## 2. Network Access Control

NAC solutions are a crucial part to network security, and of course that's what I use them for too. However, I have to point out that NAC also just makes moving devices **so easy**. 

Back when I worked for an ISP and we were cutting over customers between switches, I had to make sure to move every single cable exactly 1:1 from the old switch to the new switch, because at the time, they did not have a NAC solution. This can lead to customers that get accidentally disconnected or, such as one time, every single customer being placed into the wrong port. We were moving from a Juniper switch to a Cisco, and while Cisco starts numbering their ports with "1" - Juniper starts at "0" - so every single customer needed to be moved by one port.

Using NAC, though, I can move any cable to any port and not worry about it in the slightest. When the device connects, the switch sends a RADIUS request to the NAC server, which tells the switch what VLAN the device should be on, and tah-dah. That device is now on the correct network without me needing to even think about it.

That also makes the initial configuration of the switch a lot easier, because I can configure every switch the same and not need to worry about migrating (and translating) the old config to the new switches. That does bring up another point, though.

## 3. Preparation

In order to have a successful cutover and maintenance, you need to do some thorough preparation.

Before I even touch the existing switch, I make sure to configure and verify every aspect of the new switch going in. Once the config looks good, I get the new switch physically mounted into the rack and powered on. If I have extra fiber available, I'll connect it to the network too. If not, I'll just run a temporary cable from the existing switch to the new one so I can get it online and test its functionality.

I'll check that NAC is working correctly by moving over a single device I know nobody is using, and see if it gets assigned the correct VLAN. I'll make sure that the RADIUS admin login is working, I'll check that all the VLANs are tagged in the right spots and that traffic is flowing. Basically, I'll check everything I possibly can to ensure that the cutover will be seamless.

One thing to check for is to make sure there's no weird devices on the old switch that I need to worry about. Over the 20+ years that this building has been open 24/7, network admins of the past have made some very-permanent temporary fixes. Sometimes that's disabling NAC on a port for one device instead of configuring a profile for it. Other times that's an unmanaged switch in the wild that the new client limit config will break. Whatever it is, I make note of it and plan accordingly.

When all is said and done, it's time to start moving cables.

## 4. I show up early

Like six months ago, I actually changed my schedule to be the earliest one in the office. This isn't for some "the grind don't stop" reason but actually for two parts: Firstly, it matches better with my partner's schedule and secondly, I can get network maintenance done before most people get into the office.

The majority of people working the night shift at the casino are not ones who work in offices at workstations. It's restaurant servers, bartenders, security, dealers, cashiers, slot attendants, etc. During the week, and during the day, is when the offices are in use, and that's who will really notice network maintenance. Unfortunately, I also work during the week and during the day, so I started coming in early in order to get ahead of everyone else and cause as little interruption as I can.

It's also just nice to have some peace and quiet in the office sometimes.

## 5. When all else fails, just warn people like normal

There are some parts of the casino that just *can't* have downtime, and I need to be able to work with that. When I need to disconnect certain devices for any amount of time, I make sure to inform those that it will impact, let them know what I'm doing and why, and how long they can expect interruption for.

In my experience, this often works better than just trying to be fast about it. Every single time I've called up a user and said "hey, I'm in the IDF and I'm going to take your device offline for a minute or two," they've always just gone "okay, thanks for letting me know."

Nobody has ever gotten upset about it or demanded to speak to my manager. It's literally that simple: just tell people.

# When things go wrong

In my job, I'm dealing with 20+ years of infrastructure, and probably one of the most diverse mixes of client devices of any single building. Everything is always online all the time, and therefore, things are bound to break here and there. With every mistake, though, comes an opportunity to learn and I feel that I've really learned a lot in the last year that I've been doing this. Here's a list of some of my memorable oopsies that I now know to watch out for:

1. I tagged the VLANs *on* the new switch, but not *to* the new switch.
2. I forgot to trust the uplink port for dhcp-snooping, and thus no devices would get DHCP
3. I once incorrectly thought a switch was NAC-enabled when it was not, and ended up breaking access control for all executives of the company
4. I moved an unmanaged switch to a port with a client limit of 2 and couldn't figure out why just one of the three PCs in an office wouldn't connect.
5. I forgot to create a role on the switch for HVAC equipment and didn't realize until the building maintenance department was panicking because a refrigerated room wasn't kicking on the cooling despite the temperature climbing.
6. I forgot to update a switch *before* deploying it, and so all of my preparation and careful avoidance of client downtime were in vain as I had to reboot the switch anyway and take everyone offline for 5 mins.

You might read that and go "wow, this guy seems awful at networking," but every one of these mistakes was the first and last time they happened. I learned from what I broke and now know how to avoid doing it again. Additionally, I'm the one and only network person in the entire company, so every break of the network can only be done by me.

# Conclusion

Maintaining the network of a 24-hour casino is no easy task, but you learn tricks to make it as easy and as smooth as possible along the way. From utilizing solutions that offload some of the work, to preparing as much as possible, to just simply telling people what's happening, there are ways to deal with managing this network.

I've made many mistakes while trying to do this, but from every single one I've figured out why it happened, and how I can avoid it in the future.