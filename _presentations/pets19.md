---
layout: project
title: Handoff All Your Privacy A Review of Apple's Bluetooth Low Energy Continuity Protocol
keywords: Apple, Privacy, BLE
name: pets19
conference_url: https://petsymposium.org/2019/program.php
thumbnail: true
upload_directory: /uploads/pets19
year: 2019
conference_name: Privacy Enhancing Technologies Symposium
paper_url: https://petsymposium.org/2019/files/papers/issue4/popets-2019-0057.pdf
slides: /uploads/pets20/slides.pdf
---

# Abstract
\
We investigate Apple’s Bluetooth Low Energy (BLE) Continuity protocol, designed to support interoperability and communication between iOS and macOS devices, and show that the price for this seamless experience is leakage of identifying information and behavioral data to passive adversaries. First, we reverse engineer numerous Continuity protocol message types and identify data fields that are transmitted unencrypted. We show that Continuity messages are broadcast over BLE in response to actions such as locking and unlocking a device’s screen, copying and pasting information, making and accepting phone calls, and tapping the screen while it is unlocked. Laboratory experiments reveal a significant flaw in the most recent versions of macOS that defeats BLE Media Access Control (MAC) address randomization entirely by causing the public MAC address to be broadcast. We demonstrate that the format and content of Continuity messages can be used to fingerprint the type and Operating System (OS) version of a device, as well as behaviorally profile users. Finally, we show that predictable sequence numbers in these frames can allow an adversary to track Apple devices across space and time, defeating existing anti-tracking techniques such as MAC address randomization
