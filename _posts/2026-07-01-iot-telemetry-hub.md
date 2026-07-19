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
**Stage - 3 officially started right here.**

### Stage 3 : Making our first .exe file for our Keyboard.
The main problem here was not making a .exe file. The main problem was *Communicating with AI*, I don't know how my teammate made up his mind someone he was good in talking to *AI*, so our main barrier was when ever he tried to explain his problem what he was facing in developing a .exe file. All I heard was a nonsense language *which didn't had a proper script*. So I just nodded my head and looked into the app. So I told him what all corrections to do. Soon after that he had developed a proper ideation for how to develop the .exe file and he told me it is difficult to do it with multiple languages like frontend, backend and stuff's. So soon or later I realized that we have a goated language called *python* which can literally do anything in any field. So I researched regarding this and found out a solution that you can easily convert any .html file (*professionally a webpage*) into a working .exe file using *Pyinstaller*, *auto-py-to-exe*. So I informed my teammate to do it using it, and as he is a *vibe code specialist* he was able to achieve the .html file within 2 days and conversion was way more easier than it seemed. Thanks to him!.
So we had our .exe file in our laptop, but what to keep as a icon for it? after arguing for some time, I told him to put it as you wish.

<img src="/assets/images/icon.jpg" alt="Smol.exe Icon" width="300" height="300" >

That *crazy guy* add this cat image as a icon. 
*I liked it by the way*. 

So our job was almost done. So the problem that we faced was nothing other than. If we changed the device we need to write all keys again and again. So as a guy who used keyboard its the most irritating part. So our team researched on this later we got to know that our ESP32 S-3 has something called EEPROM. which can store some amount of data in it and it was enough for us to achieve the pre stored keys. So this was the journey of our Software development

### Smol.exe file 

I am going to show the features that our Cyberdeck_os app had within it.
[homepage image]
This is how our application looked like with minimalist design with dark background and user friendly UI. 
So the main layer that you are looking at right now is the data that is stored inside the device and the greater advantage here wasss...
The user has the complete freedom to put what every combination of keys they required including the combinations like Ctrl+c, Ctrl+v, and many other key combinations. 
[key changing image]
Now I am changing the Letter A to some random letter Z.
[key changed to z]
once the user clicks *apply config* the keys gets changed to key that user changed into.
[key changed matrix image]
like this the combination of the keys that showed up will change when the thumb buttons where clicked. 
[layer 1]
when the user is writing one first layer is doesn't need to click any button.
if the user need to change the layer of keys to the next layer. He just need to the click the respective button on which he need to work. Once he clicks the second thumb button it actually activates the layer 2 keys and the keyboard will work for the layer 2 keys properly without any errors.
[layer 2] image

similarly this can be made into all other layers *layer 3 , layer 4*.
So we are providing users the freedom of how a thumb key functions if the user needs to hold and click which is not that efficent. so we gave our user the proper freedom of selecting what mode they need to type in. 
*hold mode* or *click mode* So every of my classmates other than our teammates preferred to use the click mode because in hold mode the thumba experiences the more pressure and force which they are not used into. 

All the layers of the key had individual independency of selecting their functions and we had a idea of giving the user to change the whole combinations of keys when they are multitasking when they are using it just for typing they can keep it in basic mode and when they need to do
video editing, audio editing, photo editing, Dj's, presentations, and while streaming so we gave them a option of adding up the new workspace as they need it.
[workspace image]
They just need to add a new one and write what ever they need and delete the unnecessary layers if they are created.
**This was the brief introduction regarding the software**

### How to use our keyboard and application?

you just need to connect the keyboard to your USB port of your laptop. then you need to click on Connect UART
[image of connect uart]
This is automatically search for the Device the connected and it will start communicating with it. and if the user had any changes he/she required they can change it and just need to click on Complie and flash to uplaod the changes they made into the keyboard. once its done. Your keyboard is ready to use and its very simple to setting up you keyboard.  

#### Then how to turn on the HUD overlay?

Just click on the Toggle HUD button this will automatically turn on the overlay which will be easily moveable across the window without causing any problems and the brightness level can be changed by using the HUD transparency scroll bar. which will effectively change the brightness of the HUD. 
[HUD overlay image normal]

[HUD overlay image at light display]

this overlag will not distrub you or irritate you from doing your job. but it also serves a greater purpose of this application in helping the user by helping them identifing the keys that they need.
once this is activated click on the same toggle HUD to turn it off. So its is this easy to setup the software for our keyboard. and its more simple that you think to use it.

### Final stage : Creating the Outer casing for the keyboard

You can't just carrying the electronic components without any rigid support. So I decided to make a case for it. 
So I started designing the outer case. it was really a biggest headache to reverse engineer the abnormal skeleton to make a proper outter casing for it. 
[image of the 3d model]

Even though I had my compelete attention. I forget about the clearance I had given for the buttom surface. So this print was worth more than 300rs and I really didn't whated to take the risk so I modified the model on my own using the cutter and soldering iron by making a proper case for the keyboard.
Even though I did mistake in given clearance to keep the thumb keys inside. I wasn;t able to do it properly even in making the outer chassis for it. 
So this is how ended up in making the outer chassis. 

### How did it looked after completing the project?
[final Prototype]

This was the final prototype which was really a biggest engineering challenges that I have faced recently 




