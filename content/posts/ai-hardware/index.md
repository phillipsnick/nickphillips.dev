+++
date = '2026-02-15'
draft = true
title = 'AI Rig - Cooling the GPUs'
categories = ['ai', 'homelab']
tags = ['AI', 'LLM', '3D-Printing']
+++

As an avid homelabber and subscriber to Reddit [/r/selfhosted](https://www.reddit.com/r/selfhosted/), I'd occasionally come across self-hosted AI setups for running smaller models for various tasks. Curiosity got the better of me, and after hours of research, which led to joining [/r/LocalLLM](https://www.reddit.com/r/LocalLLM/) and [/r/LocalAIServers](https://www.reddit.com/r/LocalAIServers/), I found myself planning my first self-hosted AI rig.

Many hours later, it was clear most people were running RTX 3090s for their lower price and 24GB of VRAM. One accepted eBay offer later, at £450 a card, I had two unbranded 3090s!! The catch? They were server cards with no onboard cooling.

{{< figure 
   src="gpus.jpg" 
   alt="Bare RTX 3090 GPUs" 
>}}

## Cooling

The first step was to figure out a cooling solution. I'd hoped I could simply pop the top cover off and put multiple 80mm fans on the top. Maybe 3D print a shroud. But with the cover removed, it's a fairly solid block of metal with no suitable open fins.

{{< figure 
   src="gpu-internal.jpg" 
   alt="RTX 3090 GPU with top cover removed" 
>}}

I'd seen multiple posts of 3D-printed shrouds for blower fans, but couldn't find any models for my particular unbranded GPUs.

After many more hours of research, I settled on the Misieren SHLFBFB1012EHKH302 due to its suitable size (97x97x33mm) and PWM control. £11.54 each on Amazon.

A couple of hours later, with calipers and Fusion 360, I had a 3D-printed PETG shroud.

{{< figure 
   src="shroud.jpg" 
   alt="3D Printed fan shroud" 
>}}

This model is available on [MakerWorld](#) *TODO: publish/link*

## Fan Control

Upon disassembling the GPU I noticed some smaller 4-pin headers on the PCB which look similar to previous consumer GPU fan headers I'm familiar with.

After experimenting with a micro to standard 4-pin PWM adapter, and trying fan control through both `nvidia-smi` and `nvidia-settings`, there was no PWM output on the header, and no tach reading from a questionably wired test setup.

{{< figure 
   src="gpu-4pin-1.jpg" 
   alt="Internal mini 4-pin header" 
>}}

*CAROSEL HEADER ADDITIONAL IMAGE*

Although this is still to be tested, I'll be powering these blower fans from a 4-pin Molex connector via a custom wiring adapter, as each can draw up to 2.94A, far too much for a typical 4-pin PWM header.

The PWM and tach signals will be connected to a [Corsair Commander Pro](https://www.corsair.com/uk/en/p/custom-liquid-cooling/cl-9011110-ww/icue-commander-pro-smart-rgb-lighting-and-fan-speed-controller-cl-9011110-ww) (sharing a ground with the Molex supply) and likely controlled by [CoolerControl](https://docs.coolercontrol.org/) which lets you define custom fan curves based on hardware sensors, such as GPU temperature or load.

## Full Setup

The shroud fitted with the blower fan and custom wiring adapter. Each GPU will be installed with a PCIe riser (PCIe 4.0 x16).

{{< figure 
   src="full-setup.jpg" 
   alt="Full configuration for a single GPU" 
>}}

## Parts List

| Part                                   | Qty | Price (each) | Source     | Bought      | Notes                                                  |
|----------------------------------------|-----|--------------|------------|-------------|--------------------------------------------------------|
| RTX 3090 24GB (unbranded, passive)     | 2   | £450         | eBay       | 10th Jan 26 | Passive server card, no onboard fans                   |
| Misieren SHLFBFB1012EHKH302 blower fan | 2   | £11.54       | Amazon     | 15th Jan 26 | 97x97x33mm, PWM, up to 2.94A                           |
| Corsair Commander Pro                  | 1   | -            | eBay       | -           | PWM and tach control (already owned)                   |
| PCIe riser                             | 2   | £11.19       | AliExpress | 15th Jan 26 | PCIe 4.0 x16                                           |
| Molex to fan wiring adapter parts      | 2   | -            | Spares     | -           | Powers fans directly, shared ground with Commander Pro |
| **Total**                              |     | £945.46      |            |             |                                                        |

Next up: AI Hardware