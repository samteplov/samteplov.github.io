---
layout: project
title: Reverse Engineering Apple’s BLE Continuity Protocol For Tracking, OS Fingerprinting, and Behavioral Profiling
keywords: Apple, Privacy, BLE
name: shmoocon20
conference_url: https://www.shmoocon.org/speakers/#appleble
thumbnail: true
upload_directory: /uploads/shmoocon20
year: 2020
conference_name: ShmooCon
video_url: https://www.youtube.com/watch?v=9Nfnjct0UJk
slides: /uploads/shmoocon20/slides.pdf
---

# Abstract
\
We reverse engineer several message types of Apple’s Bluetooth Low Energy (BLE) Continuity protocol, and show that they can be used for tracking, operating system fingerprinting, and behaviorally profiling users. In particular, we identify and reverse engineer seven distinct message types, most of which are sent in response to a particular user interaction with their iOS or macOS device. Through a series of rigorous tests in a radio-frequency sterile environment, we i) determine what actions are necessary to stimulate a device to transmit these messages, ii) deduce the meanings of most fields within each message type, and iii) ascertain how operating system version updates have introduced and affected each message type. Together, this information allows an adversary within BLE transmission range to determine what actions a user is making on their device, infer what operating system version they are using, and even track users despite the use of randomized BD_ADDR. Finally, we introduce, demonstrate, and publicly release the first-ever Wireshark dissector for displaying the Continuity message types we and other security researchers have reverse engineered.
