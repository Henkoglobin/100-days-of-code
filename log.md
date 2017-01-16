# 100 Days Of Code - Log

**Skipped Days:**

1. January 15, 2017

### Day 1: January 10, 2017

**Today's Progress:** Implemented [Boyer-Moore string search](https://en.wikipedia.org/wiki/Boyer–Moore_string_search_algorithm) for [Kfr Reader](https://github.com/Henkoglobin/kfr-reader).

**Thoughts:**

I wanted to remove the need to hold each and every file in memory twice (as `byte[]` and as `string`),
since the `string` representation was only needed to search for keywords. Instead, I now search in
the `byte[]` representation using Boyer-Moore string search.

I had problems with the algorithm because I only implemented the bad-character jumps at first.
This works well in some cases, but apparently the algorithm can get stuck this way.

I will need to revisit this implementation and check if it's considerably slower than the old
approach.

**Link to work:** [Kfr Reader, commit fbe6c87](https://github.com/Henkoglobin/kfr-reader/commit/fbe6c87b25a3a4b6001697db472022e6c077c635)

### Day 2: January 11, 2017

**Today's Progress:** Barely any. It took until the next day to get anything working as I wanted it to.

**Thoughts:**

Today, I got my shiny new Raspberry Pi Zero in the mail. Naturally, I wanted to test it out and so I decided that instead of coding, I would play around with the Pi and the HATs I had ordered along with it.

I actually had three goals, of which I achieved none:

1. Make the RPi Zero work over OTG
2. Get an output on my [PaPiRus](https://thepihut.com/products/papirus-zero-epaper-eink-screen-phat-for-pi-zero?variant=28041609745)
3. Get sensor data from my [Enviro pHAT](https://thepihut.com/products/enviro-phat?variant=21227156996)

I found the sensors on the Enviro pHAT most interesting, so I decided to try that first. However, I will have to solder the headers onto the board (which I could've known had I read the description on PiHut). As I'm not yet comfortable enough with soldering, I decided to postpone this project.

Next I wanted to make the PaPiRus work - this does not require any soldering on my part (given that I have a Raspberry Pi 3 lying around that has the same GPIO layout as the Zero). So I connected the screen to the board, connected it to the Pi, installed all of the software, and... it didn't work. I have found [an issue](https://github.com/PiSupply/PaPiRus/issues/61) on GitHub with the exact symptoms seen in my tests, but couldn't figure out how to solve the problems. I will try again soon with a freshly flashed Raspbian Jessie.

What was left for me to do was to make the RPi work over [OTG](https://en.wikipedia.org/wiki/USB_On-The-Go). I did not get this to work either, at least not until the following day.
I followed [these instructions](https://gist.github.com/gbaman/975e2db164b3ca2b51ae11e45e8fd40a) to configure my RPi for OTG, but could not get it to work. I missed a couple important points, though:

1. You've got to have [Bonjour](https://support.apple.com/kb/DL999) installed. Yep, the printer services stuff.
2. You've got to use the correct USB port on the RPi: They're labeled "USB" and "PWR" - you must connect your PC to the "USB" port in order to connect with the RPi.
3. You need to install a special driver. GitHub user [christophe94700](https://github.com/christophe94700) has blogged about that (in French, but you get the gist even without speaking French): [See their comment on GitHub](https://gist.github.com/gbaman/975e2db164b3ca2b51ae11e45e8fd40a#gistcomment-1788198)

With this driver, I got OTG to work on Day 3 of #100DaysOfCoding. However, I'm not quite satisfied: It seems that OTG requires the RPi to boot using an external power source (via the second USB port). Only after the Pi has booted can I connect it to my Windows PC and SSH into it from there. I would have thought that I could just power it from the PC and use it at the same time, while still having the second USB port free for any peripherals. I will look into that at a later point in time.

**Link to work:** [My tweet about me setting up my Raspberry Pi Zero](https://twitter.com/Henkoglobin/status/819286510210007045)

### Day 3: January 12, 2017

**Today's Progress:** Got OTG to work in my Raspberry Pi Zero. Also started writing a Xamarin App (which I cannot yet make public :( )

**Thoughts:**

As I spoilered in the last log entry, I got OTG to work in my Raspberry Pi Zero today by installing Bonjour on my PC, using the correct USB port on the Pi and powering it on before connecting to the PC.

However, the main achievement for this day was that I started to work on a new side project: Twitter user [@jerainne](https://twitter.com/jerainne) came to me with a pretty cool app idea and I started work on a prototype.
I cannot yet talk about the app itself (because @jerainne might want to keep it a secret ;) ), but I hope that I will learn a lot during creation of the prototype.

The app will be implemented in Xamarin.Forms using the [MVVM](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93viewmodel) architectural pattern. It will also feature a backend written in C# using ASP.NET Core.

Today, I implemented the very basics for the app, including some "bootstrapping" code for Commands (which I wouldn't have to write if I used a framework like [MVVM Light](http://www.mvvmlight.net/)) and a service for navigation.
I am quite proud of my `NavigationService` and might blog about it in detail in the following days.

**Link to work:** None, unfortunately :(

### Day 4: January 13, 2017

**Today's progress:** Implemented a new service to locally save and load data in a Xamarin App.

**Thoughts:**

Today, I wanted to implement basic read/write facilities for the app which I will codename "Project SK" from now on. In Project SK, users are able to save notes, kinda like in a basic "Todo App".
These notes will eventually be synced via a central server. For the moment, however, I decided to just test the interface and implement a service to store notes locally.

Thankfully, I did not have to implement file access per-plattform (as I would normally have to). Instead, I was able to use the awesome [PCLStorage](https://github.com/dsplaisted/PCLStorage) library.

**Link to work:** None, unfortunately :(

### Day 5: January 14, 2017

**Today's progress:** Fixed some bugs in Project SK

**Thoughts:**

When I implemented the service stub for storing and fetching notes in Project SK yesterday, I had problems with ADB on my PC (because I was working on my private PC rather than on my work PC). 
This prevented me from testing the app. Today, however, I could solve the problems (by deleting the app from my phone - sometimes it's as easy as that).

Finally able to test the app, I was able to fix a couple of bugs. With the app now working, I was able to show it to [@jerainne](https://twitter.com/jerainne) to get some early feedback :)

**Link to work:** None, unfortunately :(

### Day 5.5: January 15, 2017

**Today's progress:** Skipped this day.

**Thoughts:**

I have skipped coding this day due to various reasons - mainly because I was too tired to do anything (and I didn't get anything done in the household either). 
I will be back to coding tomorrow, though! :)

**Link to work:** None, unfortunately :(
