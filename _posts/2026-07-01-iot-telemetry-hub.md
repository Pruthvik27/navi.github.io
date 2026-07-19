---
layout: post
title: "Project - SMOL"
---

# Project - SMOL : A keyboard 
*Date: July 19, 2026*

# While you are doing "Click, click" on your keyboard. Have you ever felt?
**"OH SHIT, IT'S THE SAME DESIGN FROM 1947?"**

**To Solve this Issue Me and My team came up with a solution**

**SOLUTION** - What if we use a clever grid layout and special "shift" buttons to pack a massive keyboard into a pocket-sized device?

**That's how - SMOL keyboard born.**

### How we approached the Problem?

Initially, I thought it was a dream project and actually building it was something that only happened in my dreams. Then there was an announcement in the class. For our ARM Programming Course, we had to make a real, working engineering Project. 
*A hardware one* 
*Not the same basic school project... Battery sarrrr.... motor sarrrr... juii.. juiii*
**It was quite different. **  

**Step 1**
We had a genius shortcut idea. Instead of wiring 80 separate buttons (which would take too many wires), we arranged the keys in a *4-row by 4-column grid (a 4x4 matrix)* using only 8 wires. Then, we added *4 mode-switching buttons* (like the Shift key on your laptop) to change what those keys do, giving us 80 total combinations!

**(4x4)x(4+1) = 80.**

Initially we had a Team of four. Then one guy gave up, because I was asking *too much* work. 
*Nah man, I was just asking for on-time submission*
*As it was complex to do within such less time as we had*

Then we had a meeting among 3 of us.
Soooo where to start this.

Initially what we thought was to add a small TV screen (TFT display) along with the keyboard. That way, the user can easily see exactly what they are typing.
*Buttttttttttttttttttttttttt.... We had a problem*
Our main computer chip (the ESP32-S3) has a major communication glitch with the screen. They speak different languages and fight with each other.
*I got to know regarding this the hard way in a past Hackathon (HUGE MISTAKE)*

Later we decided, OKAY we will first build the core keyboard. Then we will think about the extra visual things that aren't necessary right now!

So as a System Design Lead and Team lead. I did the same thing that every other team leader does...
*Assigning the roles among 3 of us*
Since I had a crystal clear picture in my head of what we needed to build, I felt a spark inside me telling me to just start creating. I directly grabbed some electronic testing boards (breadboards), some tiny push-buttons (tactile keys), and a bunch of connecting wires.

It didn't even work properly. The first row of keys worked perfectly, but the moment I tried to click anything on the next rows, the whole system got confused. The buttons wouldn't even respond to my clicks. After debugging the whole Project and tearing my hair out, I learned a massive lesson:
*Why Diodes matter the most (Think of a diode as a one-way turnstile gate for electricity)*

**Without Diode** 
*Leaving these out causes three major disasters in a grid keyboard:*
1) Electrical "bleeding" - Without a one-way gate, electricity is free to run backward. When you press Button 1, instead of the signal going straight to the computer chip, the electricity flows backward into all the nearby switches and messes up the whole grid.

2) Ghosting - Our brain chip (ESP32-S3) gets completely confused because electricity is leaking everywhere. The chip starts registering a "ghost" keypress—meaning it thinks you pressed a button that you *DIDN'T EVEN TOUCH*.

3) Masking - Because the leaked electricity is flooding the system, it acts like blinding headlights. If you press multiple keys at the same time, the chip gets blinded and completely ignores your real, legitimate keypresses.

*So using the Diodes, "A simple one-way gate" for each switch kept the signals separated, stopped the leaks, and gave my project a new life.
