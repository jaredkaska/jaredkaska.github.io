--- 
title: "Modems Shouldn't Exist"
date: 2026-04-03 
categories: [Internet, Thoughts] 
tags: [isp, cable, dsl, fiber] 
---

This might sound like a pretty strange title, but I swear it makes sense. This concept is like my party trick conversation to have when chatting about networking and home internet. It always catches people off guard and they usually find it pretty interesting. At least, I think so.

## What is a modem?

Have you ever thought of the word 'modem' and wondered what on earth it actually means? Maybe you're trying to figure out the root words and relate it to other things you know. Here's a secret, though. 'Modem' is not a word. It's just a shortened version of two words: **mo**dulate and **dem**odulate. That's it.

It really just means creating a signal, and interpreting a signal.

Modems are used for your home internet primarily if you have dial-up, DSL, or cable internet, because you need some way to send and receive the radio signals for DSL and cable, or the actual sounds for dial-up. But why do we have to convert the data into some other medium like this in the first place? Well, that brings me to my next point.

## Most internet service doesn't have dedicated infrastructure

This point was a lot more true maybe 10 or 20 years ago. It has certainly gotten better these days, but it's still a long way off. From a quick Google search, about 50-60% of US households use cable for their home internet.

What do I mean by "dedicated infrastructure", though? Think about this: power has their own power lines, telephone uses twisted-pair telephone wires, and television uses coaxial cable. You'll often see all three of these separate cables on the poles down your street. Internet, though? It uses whatever it can get its hands on.

Basically, demand for internet spiked so fast, demand was so high, that providers just threw it onto their existing infrastructure to get it out there fast.

Dial-up doesn't even have much additional infrastructure to get the job done. Your modem just makes a phone call to some server which actually connects to the internet, and exchanges information through sound.

DSL is a little better, utilizing a DSLAM (DSL Access Multiplexer) to add internet connection onto existing phone cables at a different frequency.

Cable is currently what half of the US has, using the DOCSIS (Data Over Cable Service Interface Specification) standard, and a CMTS (Cable Modem Termination System) to add internet connectivity to television cables.

## What's wrong with these solutions?

Since these solutions were not built with internet in mind, they have their drawbacks. The biggest of which is probably distance. On copper cables (or literally anything conductive), the further signal travels, the higher the resistance is. Over longer distances, signals will get weaker or more distorted, limiting the range and speed of internet connectivity.

Dial-up is able to travel the longest distance, as it just uses sound which the telephone wires were already designed for. However, as you may have noticed, it is not at all fast. You can only send so much information at once using sound.

DSL is faster, but since it's sending more information at a higher frequency, it is more prone to distortion and signal loss over long distances. So while it is available in *many* areas that have telephone wires, it is not available in all. This also means your internet speed over DSL is completely dependent on how close to the DSLAM you are, with the upper limits being about 2km.

Cable is actually lightning fast, or at least has the potential to be. The DOCSIS technology has been the most developed of the three of these examples by far. Without getting into the specifics of how DOCSIS works (which I absolutely can in another post), cable has the potential to do multi-gigabit speeds up and down, which is far more than most people will ever need at home. However, the distance it can travel is much shorter, requiring powered amplifiers placed regularly along the cable. This also makes it the most expensive to build new sections, which is why it may have taken years for it to finally come up your street even if it's less than a mile away.

With all of these, another large issue is that copper corrodes. Like, a lot. These networks require lots of routine maintenance to keep them up and running, and can be affected by so many more outside factors that you would never expect. Bad connections, the temperature, water in the cable, even your neighbor running an old saw can take out your internet.

## So what is the perfect solution?

If you haven't guessed it by now, the real, actual, correct solution to home internet access is fiber optics. This is simply shining a light down a glass tube, and that's it. Okay, there's a little more to it than that, but the actual infrastructure in neighborhoods is way simpler than with any of these other solutions.

Fiber is also very cheap and easy to maintain once it's built. It's not affected by temperature, interference, and the speed at which data can travel across it depends on the devices at the ends, not necessarily the fiber itself. Therefore, you can throw fiber in the ground and your infrastructure can continue to evolve without needing to replace the fiber.

*So wait, why on earth have we not adopted fiber everywhere, to every home?*

Well, it's expensive.

*But I thought you just said it's cheap and easy.*

I did, let me explain.

I said fiber is cheap and easy to maintain **once it's built**. The upfront cost for building fiber, though, can be very expensive. This large price tag is what's keeping internet providers from going all-in and building the stuff everywhere. It's much cheaper for them to keep maintaining their existing coaxial cable networks.

Well, except it's not. It's cheaper in the short term, but over a longer time, the labor and material costs for cable is easily higher than fiber. So fiber really is the smart investment, but it seems some ISPs are still hesitant. In my area, Ziply Fiber is definitely not - the guy who started it used to be the CEO of another local cable company, and he saw the value in fiber. He sold the cable company and founded Ziply Fiber and just went absolutely crazy with building fiber optics everywhere. And let me tell you, their internet service is awesome, and they're absolutely dominating the competition.

## So, why shouldn't modems exist?

Modems shouldn't exist because they are a band-aid solution. They're the equivalent of an IOU instead of getting paid. They're like getting a loaner car at the dealership while yours is in the shop.

Modems were created because we needed a quick solution to get internet to everyone until we can work out the real infrastructure, like fiber. In the decades that followed, though, providers realized it's cheaper (at least short term) to *not* build that new infrastructure and to just keep maintaining the existing cable network, evolving new technologies like DOCSIS 4.0 to still compete without doing the work to actually provide the same service as fiber.

You know what they say. There's nothing more permanent than a temporary solution that works.