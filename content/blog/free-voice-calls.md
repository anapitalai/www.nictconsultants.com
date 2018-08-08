---
title: Free Voice Calls
author: Alois Napitalai
date: '2018-08-08T12:39:18+10:00'
image: /images/aster.png
---
Free Call Over the Local Area Network(ASTERISK)

Two years back I tried toying around with this open-source software and managed to get two phones making voice call to each other via a asterisk server connect to a LAN. I had some thoughts just the other day to try and redo what I did earlier and I accomplished that but this time added sms messaging,voice-mail and video calls.The heart of this software is dial-plans and extensions. If you are familiar with programming then that is what a dial-plan really is, it is a parsed scripting language like other languages like PHP,python,bash,etc but not interpreted or compiled like java or C++. It provides the logic of the system.Extensions are the identifiers created for individual phones in asterisk and configured in the devices. In this setup, I configured four SIP accounts in asterisk and then used sip soft-phones(zoiper) to make the calls.One disadvantage of VOIP is that it uses the UDP protocol for realtime communication hence there is no guarantee that a packet reaches it destination and too no retransmission when a packet is dropped along the way.This results in jitters or broken or delayed audio and video or sms drops. My next plan is to get this setup and configure it on a Virtual Private Server so it sits in the cloud and can be connected to it from anywhere provided you have Internet connection.One hurdle I anticipate will be trying to connect phones from behind a NAT or proxy server or firewall.

Sample extensions.conf with voice-mail and extension

[users]

exten=>2000,1,Dial(SIP/2000,20)

exten=>2000,n,VoiceMail(2000@vm-demo,u)

exten=>2001,1,Dial(SIP/2001,20)

exten => 2001,n,VoiceMail(2001@vm-demo,u)

exten=>2002,1,Dial(SIP/2002,20)

exten => 2002,n,VoiceMail(2002@vm-demo,u)

Sip.conf

[2000]

type=friend

host=dynamic

secret=2000

context=users

nat=force_rport

qualify=yes

disallow=all

allow=ulaw

allow=alaw

allow=vp8

allow=h264

allow=h263p

videosupport=yes
