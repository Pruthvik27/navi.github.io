---
layout: post
title: "Project SMOL: A keyboard"
permalink: /project-smol/
---

# Project - SMOL : A keyboard 

# While you are doing "Click, click" on your keyboard. Have you ever felt?
**"OH SHIT, IT'S THE SAME DESIGN FROM 1947?"**

**To Solve this Issue Me and My team came up with a solution**

**SOLUTION** - What if we use a clever grid layout and special "shift" buttons to pack a massive keyboard into a pocket-sized device?

**That's how - SMOL keyboard born.**

### How we approached the Problem?

Initially, I thought it was a dream project and actually building it was something that only happened in my dreams. Then there was an announcement in the class. For our ARM Programming Course, we had to make a real, working engineering Project. 
*A hardware one* 
*Not the same basic school project... Battery sarrrr.... motor sarrrr... juii.. juiii*
**It was quite different.**  

### **Step 1**
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

*So using the Diodes, "A simple one-way gate" for each switch kept the signals separated, stopped the leaks, and gave my project a new life.*

**So I completed the breadboard Prototype**

<img src="/assets/images/Breadboard_prototype.jpeg" alt="Breadboard Prototype" width="400" height="300">


## As everyone does, I moved on to making a perfboard Prototype 

Once the temporary breadboard version worked, I immediately started building the permanent version on a circuit board with holes (a perfboard). I had done some soldering before, but... 
*I never knew that wire insulation melts instantly if a hot soldering iron touches it for more than 10 seconds...*
To make things worse, I was so clueless that I accidentally bought a cheap perfboard that only had copper rings on one side, leaving the other side completely blank, so the melted metal glue (solder) had nowhere to stick. 

After soldering the keys in place, I decided to give it a test run. Everything seemed fine initially, but then I accidentally melted 2 of the keys while soldering the connecting wires. Because of that mistake, I lost the solid mounting points needed to hold my custom buttons in place. 
I had no choice but to rip them out and swap them with fresh keys. Finally, after *breathing in way too much toxic soldering smoke*, the perfboard prototype was successfully finished!


<div style="display: flex; gap: 30px; justify-content: center; align-items: center;">
    <img src="/assets/images/Perfboard Prototype Front.jpg" alt="Perfboard with Keys" style="width: 50%; height: 600px; object-fit: cover;">
    <img src="/assets/images/Perfboard with diodes.jpg" alt="Perfboard with diodes" style="width: 50%; height: 600px; object-fit: cover;">
</div>

**SO the prototype was working fine and it was a success.**

*But you can't type comfortably with sharp, exposed wire needles hurting your fingers.*

## So Hardware designing time
It was time to design custom plastic keycaps from scratch using a 3D modeling software called Fusion360. 
*Why didn't I use Solidworks instead?*
*Simply because I wasn't fast or fluent enough with it yet to design keys on a tight deadline.*

So I jumped right into designing my very first keycap concept. 
Before even sending it to the printer, I had mentally resigned myself to burning through our team's tiny project budget by designing a complex mechanical part—completely ignoring the technical limitations of the 3D printers available in our college lab.
*Seriously, I had absolutely zero knowledge about 3D printing tolerances (the tiny gaps needed for parts to fit together) or the technical settings they used.*

Finally, I finished my first keycap design.

<img src="/assets/images/key model- 1.png" alt="My first keycap design">

My teammate worked incredibly hard navigating the chaotic paperwork to get the parts printed on the newly set up lab printers. 

After waiting in anticipation for a whole week... 

**I got this**

<img src="/assets/images/Key Iteration - 1.jpeg" alt="My first keycap Result"  width="300" height="300">

I already know exactly what you are *thinking right now* after looking at that disaster.

### So I decided not to give up and decided to redesign with the proper precautions and the same procedure again.


<img src="/assets/images/key model - 2.png" alt="My second keycap design">

  
Once again, my poor teammate had to run around campus to secure approvals, process payments, and jump through all the administrative hoops required just to use the 3D printer. 

Then, this is what came out... 
*AGAINNNNNNNNN....*


<img src="/assets/images/Key iteration - 2.jpeg" alt="My second keycap Result" width="300" height="300">

I know what you are thinking again. It was almost perfect, but an accidental dip on the top surface ruined the entire aesthetic. Even worse, the keycap was way too short, making it wobble uncontrollably with zero stability while trying to type.

### So instead of Again burning my team budget. 
**I went to design the new keys**

I was on high alert during this third design phase because I absolutely refused to waste my teammates' hard-earned money a third time. For once in my lifetime, I stopped taking things for granted and got completely serious about the engineering details.

I redesigned the prototype from scratch. It looked something like this: 

<img src="/assets/images/key model - 3.png" alt="My third keycap design">

With the design finalized, I crossed my fingers tightly, double-checking everything to see if I had missed any hidden flaws. After waiting another long week, I finally got the final print:

<img src="/assets/images/key iteration - 3.jpeg" alt="My third keycap Result" width="300" height="300" >

The result was incredibly satisfying! It perfectly fixed all of my previous design mistakes. Just like that, the longest and most frustrating phase of the project, which dragged on for a whole month, finally came to an end.

Then,
Two major milestones were complete, but we were still completely stuck staring at each other, thinking: 
*"Should we add a TFT display screen or not?"*
**OR**
*"If I add the TFT display, the whole system crashes and stops working entirely."*

After hours of intense brainstorming, I glanced at my laptop screen and noticed how I track my CPU and graphics card temperatures. It sits quietly on the screen without blocking my view, yet gives me all the vital information I need instantly.

That sparked our final breakthrough idea: we would develop a custom 
*ON-SCREEN SOFTWARE OVERLAY*
Since I couldn't physically fit 80 different labels onto a tiny pocket-sized keyboard, a smart digital overlay was the perfect solution. It would pop up on the user's computer screen to show them exactly which typing "layer" they were using and what characters they were pressing in real-time.

With the plan set, I immediately contacted my Software Lead—a guy who possesses world-class expertise in *VIBE CODING* (writing code purely by gut feeling and chaotic energy). And just like that, 

### Stage 3 : Making our first .exe file for our Keyboard.

The main problem here wasn't making the .exe file — it was *communicating with AI*. I'm still not sure how my teammate convinced himself he was good at talking to AI, because every time he tried explaining the problem he was facing, it came out as a jumble with no real structure. So I'd just nod, dig into the app myself, and tell him what corrections to make. Once that clicked, he had a clear idea of how to build the .exe, but he told me it was tricky since it needed multiple languages — frontend, backend, and more.

That's when I remembered we have a goated language called *python*, which can basically do anything in any field. A bit of research turned up the answer: you can convert any .html file (*basically a webpage*) into a working .exe using *Pyinstaller* and *auto-py-to-exe*. I passed this on to my teammate, and since he's a *vibe code specialist*, he had the .html file ready in 2 days — the conversion to .exe turned out way easier than expected. Thanks to him!

So we had our .exe file, but what to use as the icon? After some back and forth, I told him to just put whatever he wanted.

<img src="/assets/images/icon.jpg" alt="Smol.exe Icon" width="300" height="300" >

That *crazy guy* picked a cat image as the icon.
*Honestly, I liked it.*

So our job was almost done. The only real problem left was that every time we changed devices, we had to write all the keys again — which, as someone who uses a keyboard daily, is the most irritating part. Our team researched this and found out our ESP32-S3 has something called EEPROM, which can store enough data for us to keep the pre-stored keys permanently. And that was the end of the software development journey.

### Smol.exe file 

Here are the features that our Cyberdeck_os app has.

<img src="/assets/images/Homepage.png" alt="Homepage" width="500" height="500" >


This is how our application looks — a minimalist design with a dark background and a user-friendly UI.
The main layer you're looking at is the data stored on the device, and the best part is —
The user has complete freedom to set any combination of keys they want, including combos like Ctrl+C, Ctrl+V, and more.

<img src="/assets/images/keys with ctrl and space.png" alt="Ctrl and Space operation" width="500" height="500" >

Here I am showing you how ctrl and Space can be assigned to the keys.

<img src="/assets/images/keys with ctrl and space.png" alt="Ctrl and Space operation" width="500" height="500" >

Here I'm changing the letter A to some random letter Z.

<div style="display: flex; gap: 20px; justify-content: center; align-items: center;">
    <img src="/assets/images/letter A.png" alt="Inital config" style="width: 48%; height: 250px; object-fit: cover;">
    <img src="/assets/images/letter Z.png" alt="Modified config" style="width: 48%; height: 250px; object-fit: cover;">
</div>

Once the user clicks *apply config*, the keys change to whatever was set.
Similarly, the combination of keys shown changes when the thumb buttons are pressed.

<img src="/assets/images/layer 1.png" alt="Layer - 1" width="400" height="400" >

*Layer - 1 image*

When typing on the first layer, the user doesn't need to press any button.
To switch to the next layer, the user just presses the respective thumb button they want to work on. Once the second thumb button is pressed, it activates Layer 2 keys, and the keyboard works properly on Layer 2 without any errors.

<img src="/assets/images/layer 2.png" alt="Layer - 2 " width="400" height="400" >

*Layer - 2 image*

The same applies for all other layers — *Layer 3, Layer 4*.

We also gave users the freedom to choose how the thumb keys function — whether they want to hold and click, which isn't very efficient, or use a proper toggle. So we gave them the option to choose their preferred mode: *hold mode* or *click mode*. All of my classmates other than our teammates preferred click mode, because in hold mode the thumb experiences more pressure and force than they're used to.

<img src="/assets/images/toggle.png" alt="Toggle Option" width="400" height="400" >

*Toggle Option image*

Every layer of keys had its own independence in choosing its function, and we added the ability to switch entire key combinations depending on what the user is doing. For basic typing, they can stay in basic mode, and when they need to do video editing, audio editing, photo editing, DJing, presentations, or streaming, they can add a new workspace as needed.

<img src="/assets/images/workscape.png" alt="Workspace" width="400" height="400" >

*Workspace Image*

They just need to add a new one, set up what they need, and delete unnecessary layers if created.

**This was the brief introduction to the software.**

### How to use our keyboard and application?

You just need to connect the keyboard to your laptop's USB port, then click on Connect UART.

<img src="/assets/images/UART.png" alt="Connecting the device to the application" width="400" height="400" >

*Connecting the device to your laptop*

This automatically searches for the connected device and starts communicating with it. If the user needs any changes, they can make them and just click Compile and Flash to upload the changes to the keyboard. Once that's done, your keyboard is ready to use — it's that simple to set up.

#### Then how to turn on the HUD overlay?

Just click the Toggle HUD button, and the overlay turns on automatically. It's easily moveable across the window without any issues, and the brightness can be adjusted using the HUD transparency scroll bar.

<div style="display: flex; gap: 20px; justify-content: center; align-items: center;">
    <img src="/assets/images/normal.png" alt="Normal HUD" style="width: 48%; height: 250px; object-fit: cover;">
    <img src="/assets/images/light.png" alt="HUD after adjusted" style="width: 48%; height: 250px; object-fit: cover;">
</div>

This overlay won't distract you or get in the way of your work — but it also serves a bigger purpose by helping the user identify the keys they need. Once activated, click the same Toggle HUD button to turn it off. That's how easy it is to set up and use our software.

### Final stage : Creating the Outer casing for the keyboard

You can't just carry the electronic components around without any rigid support. So I decided to design a case for it.
Reverse-engineering the odd skeleton of the board into a proper outer casing turned out to be the biggest headache of this stage.

<div style="display: flex; gap: 20px; justify-content: center; align-items: center;">
    <img src="/assets/images/chassis 1.png" alt="Outer case bottom" style="width: 48%; height: 250px; object-fit: cover;">
    <img src="/assets/images/chassis 2.png" alt="Outer case enclosure" style="width: 48%; height: 250px; object-fit: cover;">
</div>

Even with my full attention, I forgot to account for clearance on the bottom surface. That print cost over ₹300, and I didn't want to risk another failed print, so I fixed the model myself using a cutter and soldering iron to build a proper case for the keyboard. I also underestimated the clearance needed for the thumb keys, so even the manual fix for the outer chassis wasn't perfect.
Still, that's how I ended up completing the outer chassis.

### How did it look after completing the project?

<img src="/assets/images/Final.png" alt="Final Design" width="400" height="400" >

This was the final prototype, and honestly one of the biggest engineering challenges I've faced recently. So to conclude on this project. I would like to tell.

*Nothing is impossible, if you have a great team which are damn responsible*

### Welcome the Team

**System design and Team Lead** - Myself - Pruthvik S
**Procurement and Electrical Lead** - Pratik Jadhav 
**Software and embedded lead** - Narendrababu N Bisleri

I don't know how to thank them. But they put there maximum efforts into this by achieving, what I thought it was impossible to do. 

### Thanks for reading this! If you like it please share it among your mates 


You can download the complete files and information here: [📁 See complete information on  Google Drive]([https://drive.google.com/file/d/your-actual-link-here/view?usp=sharing](https://drive.google.com/drive/folders/1SsLlahhHt4yO5CBT87uLKQ1MaEx5zKag?usp=sharing))




