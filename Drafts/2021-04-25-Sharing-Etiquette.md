---
layout: post
title: Sharing Etiquette
description: Exploiting vulnerabilities in Cellebrite UFED and Physical Analyzer from an app's perspective
summary: moxie0 on 21 Apr 2021
tags: [Tech, Rumination]
---
Cellebrite makes software to automate physically extracting and indexing data from mobile devices. They exist within the grey – where enterprise branding joins together with the larcenous to be called “digital intelligence.” Their customer list has included authoritarian regimes in Belarus, Russia, Venezuela, and China; death squads in Bangladesh; military juntas in Myanmar; and those seeking to abuse and oppress in Turkey, UAE, and elsewhere. A few months ago, they announced that they added Signal support to their software.

Their products have often been linked to the persecution of imprisoned journalists and activists around the world, but less has been written about what their software actually does or how it works. Let’s take a closer look. In particular, their software is often associated with bypassing security, so let’s take some time to examine the security of their own software.

## The background

First off, anything involving Cellebrite starts with someone else physically holding your device in their hands. Cellebrite does not do any kind of data interception or remote surveillance. They produce two primary pieces of software (both for Windows): UFED and Physical Analyzer.

UFED creates a backup of your device onto the Windows machine running UFED (it is essentially a frontend to `adb backup` on Android and iTunes backup on iPhone, with some additional parsing). Once a backup has been created, Physical Analyzer then parses the files from the backup in order to display the data in browsable form.

When Cellebrite announced that they added Signal support to their software, all it really meant was that they had added support to Physical Analyzer for the file formats used by Signal. This enables Physical Analyzer to display the Signal data that was extracted from an unlocked device in the Cellebrite user’s physical possession.

One way to think about Cellebrite’s products is that if someone is physically holding your unlocked device in their hands, they could open whatever apps they would like and take screenshots of everything in them to save and go over later. Cellebrite essentially automates that process for someone holding your device in their hands.