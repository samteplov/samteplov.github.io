---
layout: project
title: Reverse Engineering Apple's BLE Continuity Protocol
quote: The journey of reverse engineering Apple's proprietary BLE protocol.
keywords: Apple, BLE, Continuity, Handoff, Privacy
thumbnail: true
upload_directory: /uploads/apple-ble-project
github_url: https://github.com/furiousMAC/continuity
status: active
---

# Quick overview
\
This project is a result of [Furious MAC's](https://furiousmac.com/) 2019 Proceedings on Privacy Enhancing Technologies (PoPETS) publication *[Handoff All Your Privacy – A Review of Apple’s Bluetooth Low Energy](/publications/handoff-all-your-privacy/)*. I presented this work at [ShmooCon 2020](https://www.youtube.com/watch?v=9Nfnjct0UJk). You can find the most up-to-date Wireshark dissectors [here](https://github.com/furiousMAC/continuity).



<!--more-->

# Background
\
Apple has long strived to deliver a seamless user experience for their users. Since most users have more than one Apple device, Apple developed a protocol to help transfer data between devices. This protocol is called [Continuity](https://support.apple.com/en-us/HT204681) and runs over Bluetooth Low Energy (BLE). Continuity supports a number of popular features such as  Handoff, Universal Clipboard, Auto Unlock, AirDrop, and more.


The initial research for this project started back in 2017 with the [Furious MAC](https://furiousmac.com/) research group. After publishing *[A Study of MAC Address Randomization in Mobile Devices and When it Fails](https://arxiv.org/pdf/1703.02874.pdf)* in PoPETS 2017, the group wanted to see if the same privacy concerns existed in BLE. Right from the start, it was evident that the majority of BLE traffic in the wild was coming from Apple devices. Since all BLE advertisement frames contain a Company ID field, it was trivial to filter on Apple's Company ID ```0x4C00```. When we started analyzing Apple's BLE traffic in Wireshark, everything after the Company ID field did not dissect; it was just unknown advertisement data. We did note, however, that some parts of the unkown data would stay constant even when the BLE MAC address would rotate. This meant that users could be tracked even though Apple implemented BLE MAC address randomization per the [BLE spec](https://inst.eecs.berkeley.edu/~ee290c/sp18/note/BLE_Vol6.pdf).

Eventually, we became more interested in the actual data that the devices were sending out than the fact that some values were staying static across MAC address changes. Using a RF sterile environment, we started on the long and tedious journey of black-box reverse engineering every message and field. By carrying out specific user actions on various Apple devices, we were able to learn a majority of the different messages, fields, and possible values. As we learned more and more of the different messages and fields, we would update our Wireshark dissector and recompile it.

# Current Work
\
After our 2019 PoPETS publication, we continued to work on reverse engineering more fields and messages. There were a number of other researchers that also came out with [publications](https://petsymposium.org/2020/files/papers/issue1/popets-2020-0003.pdf), further detailing more fields and messages that we missed. In January of 2020, I presented at [ShmooCon](https://www.youtube.com/watch?v=9Nfnjct0UJk) and we released our custom Wireshark dissector publicly for the first time. Since then, we have continued updating our Wireshark dissector and all of the latest code changes and updates can be seen on our [Github Repo](https://github.com/furiousMAC/continuity). Apple has yet to fix any of the privacy concerns or tracking vulnerabilities which we disclosed back in 2019, and other researchers have reemphasized and found more vulnerabilities in [recent work](https://petsymposium.org/2020/files/papers/issue1/popets-2020-0003.pdf).


# Future Work
\
We are continuing to update the dissector as new versions of iOS and MacOS are released by Apple. Eventually, our goal is to merge our custom dissector into the main Wireshark branch. That way, everyone would be able analyze Apple BLE advertisements without needing to download our custom dissector and recompile Wireshark.
