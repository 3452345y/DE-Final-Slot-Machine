# Pi-Top Slot Machine 
Physical Slot Machine built on Raspberry Pi / Pi-Top
[![Watch the demo](https://img.youtube.com/vi/NY_GW2emXRA/maxresdefault.jpg)](https://www.youtube.com/watch?v=NY_GW2emXRA)


## Introduction
I took on this project because there has been an epidemic of online gambling and betting that has only become more prevalent in recent years. I wanted to make something to show people not to gamble, because the odds are in the house's favor and you will always lose out in the long term. By building a physical slot machine using a pi-top I could allow people to gamble without actually losing real money.


## Block Diagram
The Design Process began with mapping out the flow of the code on paper, which helped me to visualize how it would look once completed. This is the block diagram after two revisions.
![Block Diagram](https://github.com/3452345y/DE-Final-Slot-Machine/blob/main/Github%20Images/Explain%20a%20step%20or%20phase%20(1)%20(1).png)


## Features
* Ultrasonic sensor to detect prescense

![Ultrasonic Sensor](https://github.com/3452345y/DE-Final-Slot-Machine/blob/main/Github%20Images/ultrasonic_sensor.png)

* Button for user input

![Button](https://github.com/3452345y/DE-Final-Slot-Machine/blob/main/Github%20Images/button.png)

* Adjustable bet with potentiometer
  
![Potentiometer](https://github.com/3452345y/DE-Final-Slot-Machine/blob/main/Github%20Images/potentiometer.png)

* Win Logic: Loss, Small Win (2 matching symbols), Big Win (3 Matching Symvols), Jackpot (Triple 7s)
  
* Sounds for each result


## State Machine
| State        | Description                                      |
|--------------|--------------------------------------------------|
| `IDLE`       | Waiting for someone to approach                  |
| `WELCOME`    | Player detected                                  |
| `SHOW_BALANCE` | Displays the player’s current balance         |
| `SET_BET`    | Player adjusts bet using potentiometer           |
| `CONFIRM_BET`| Bet is locked in            |
| `SPIN`       | Slot reels spin and sound plays                  |
| `RESULT`     | Shows result and win/loss before resetting to Idle       |


## Acknowledgments
This project was built using the following libraries and tools:
- **[pi-top Python SDK](https://github.com/pi-top/pi-top-Python-SDK)** - Comprehensive library for controlling pi-top hardware components including the miniscreen, ultrasonic sensor, potentiometer, button, and LEDs
- **[Pygame](https://www.pygame.org/)** - Cross-platform multimedia library used for audio playback

## Challenges
Button Debouncing - Physical button presses sometimes registered multiple times, causing the code to skip through states. To solve this, I created a `wait_for_release()` function to prevent state transitions until the button is released by sleeping for 0.01 seconds. Another Issue i faced was with the potentiometer, as the readings on it were not very reliable, and I had to map thsoe readings to the bet amouunt, so I created a function to round its values to 50. Initially I attempted to use a seperate LCD display: a LCD 1602 wired to the GPIO header, since it would have more capabilities than the pi-top display. However, I was unable to get it to work with RPLCD, a Python 3 Raspberry PI Character LCD library for the Hitachi HD44780 controller.

## Potential Improvements
Data could be stored of money won/lost overtime of the program being run, which would better illustrate the anti-gambling message. Instead of static "spinning..." text, I could animate the symbols cycling on a display to more closely mimic real slot machines. I was acutally messing with a Monochrome 0.96" 128x64 OLED, but there wasn't time to implement that.

Testing the OLED with a gif
![GIF](https://github.com/3452345y/DE-Final-Slot-Machine/blob/main/Github%20Images/uma.mp4)

MIT License

Copyright (c) 2026 Jeffrey Huang and Gavin Linang

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
