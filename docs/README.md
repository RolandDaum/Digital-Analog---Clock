# [Digital Analogue - Clock](https://rolanddaum.github.io/Digital-Analog-Clock/)

![Project Banner](https://github.com/RolandDaum/Digital-Analog-Clock/blob/main/docs/dac_banner.png?raw=true)

## Introduction
I saw this concept of a clock made out of multiple smaller analogue clocks which are then forming the digital number somewhere on YouTube or TikTok. I thought about how to do this with HTML, CSS and JS, as minimal as possible for a short moment. Then it came to my mind that I once saw a video which showed that you can animate SVG code with CSS. So no time to lose, I started coding and came up with this kinda amazing clock.
You can just use it as the [website](https://rolanddaum.github.io/Digital-Analog-Clock/) or via Wallpaper Engine on Steam [link](https://steamcommunity.com/sharedfiles/filedetails/?id=3030466464).

## Functionality
The entire thing is just one big grouped SVG file. The SVG files can be found inside the projects [/files](/files/) folder. There are 6x digits (Groups) in total starting to count at 0.
```
"Num 0", "Num 1", ..., "Num 5"
```
Each digit has the size of 2x by 3x small and simple analogue clocks. These are also numbered from left to right and top to bottom just like this
```
"C${digit_num}_${clock_num}"

"C0_0", "C0_1", ..., "C0_5"
"C1_0", "C1_1", ..., "C1_5"
```
Each clock has a minute and hour pointer named similar to the clock's group name.
```
"C${digit_num}_${clock_num}_H"
"C${digit_num}_${clock_num}_M"

"C0_0_H", "C0_0_M"

"C0_1_H", "C0_1_M"

"C1_0_H", "C1_0_M"

"C1_1_H", "C1_1_M"
```
These names of the SVG groups aren't anything else then normal HTML IDs, which means we can change their properties via
```
document.getElementById('C${digit_num}_${clock_num}_H');
```
The ten different numbers that each digit has to be able to display are stored in an array which stores each deg position of both the minute and hour pointer, which then can simply be inserted into the transform rotate property and with some CSS transition settings animated the pointers automatic.
To finally update the time every second, I'm using an interval that triggers every 1000ms and just adjust the degree of the pointer.

