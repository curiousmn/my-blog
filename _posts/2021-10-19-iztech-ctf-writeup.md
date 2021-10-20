---
layout: post
title: "Iztech Cybersec 18/10/21 CTF Writeup"
---

So 2 days ago I joined Iztech Cybersec and there was an easy ctf. Here's the writeup.

So there is a given Screen Shot which indicates a twitter account.

![Twitter SS](../../../assets/images/ctfss.png){:class="img-responsive"}

When we follow the username and go to the twitter account we are seeing 3 tweets.

![Twitter SS](../../../assets/images/ctfss1.png)

First tweet is a youtube link and it sends you to a Mr.Robot decryption scene.(Which is kinda useless)
But second tweet looks kinda suspicious. First, I thought its encoded with base64 but then I thought its looking more likely to rot13.
So I gived a shot to rot13 and "Voilà" it worked.

```
docs.google.com/forms/d/e/1FAIpQLSdcjY2KIT7k4HOQf7avE45FEGl2WSHyvKpthsy5syCAOHgGUA/viewform?usp=sf_link
```

And what's that. It's a Google forms page. And we need a key.
![Google Forms](../../../assets/images/forms.png)

Let's look at the 3rd tweet. Hmmm. It's also encoded with rot13.

```
Iztech CyberSecurity Bounty Key: 1zt3chCyb3rS3cur1ty1sS04w3s0m3
```

And after we submit the answer, it sends us to Go Playground. 
So we're given a golang code. When we run it, it returnes errors.

![Error](../../../assets/images/error1.png)

We need to define fmt. After that we're seeing a Hint:

```
Hint1: I love the mr.robot and perrin pages. But not all of them, only first 10
```

Oh there is a some lines in comment. Let's remove them.
![comment](../../../assets/images/func1.png)

We're seeing more hints. That's good.(Right Right?)

```
Hint2: How should I use this numbers? Maybe just concetenate like strings..
Hint3: Wait! This private key must be 32 bytes, how should I fill remaining part? Maybe I should add 0's for padding from left..
```
So lets find the private key.

![Key](../../../assets/images/key.png)

Let's go to the perrin pages numbers wikipage and copy the first 10 number of the sequence. Put them together like a string and add 0's to the beginning of the string until the length of string is 32 byte.
And it's done.

```
fl4g_1_4m_4_gr34t_h4ck3r_wh0_w1ll_j01n_1zt3ch_cyb3rs3c_s0c13ty
```
