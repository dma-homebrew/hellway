# Hellway V1.00 (Digital Release)

## Introduction
An Atari 2600 game, the objective is to travel the maximum distance possible, given the time limit. The game is done in 6502 assembly, and has no intention to use bankswitch or any enhancement chip, respecting the limitations of the time and a 4k ROM which the vast majority of games of the time had.

It can be played online at https://javatari.org/?ROM=https://github.com/opbokel/hellway/raw/master/bin/hellway.asm.bin

Or downloaded as a emulator compatible binnary (in the bin folder). The code will be kept open.

## License
Feel free to download, play, burn to a cartridge and have fun. The only restriction is to not sell it in order to make profit. If no profit is made or it is fully donated, I am ok with it. If you do any derivative work, please give the proper credits.

I will sell physical copies in the near future and donate every profit I made to charity projects and people in need. If you like the game, please consider doing any action to make a better day for another person or buying a copy. Also, feel free to talk about it in social medias using the hashtag #hellway2600

## Instructions
Every track has its own speed, and the car generation is deterministic. Accelerating and breaking are equally important.

The top of the screen shows the distance traveled, and also serves as a score. The second field is how much time left, and the third, is your current speed all in hexadecimal.

Every checkpoint (0x100) you receive more time, and the score and the car turn green. This will make you invincible for a few seconds. You will receive an audio alert just before it.

If the time is over the score and the car turns red, but you still can reach a checkpoint, since the car slowly decelerates.

The game is over when the time is over and the car is stopped. The score turns white.

## Switches
* Difficulty switches: They change the traffic intensity and color. The switches form a binary number representing intensity. The more traffic it has, the more time you gain on checkpoints. The constants regarding color, time and traffic are still subject to fine tuning. I tried to reduce eye strain in the color scheme. It might have slightly different effects depending on the game mode. The time added per checkpoint also varies.
    * 0 - BB = Light traffic, Green (+ 30 seconds)
    * 1 - BA = Regular traffic, Red (ish) (+ 35 seconds)
    * 3 - AB = Intense Traffic, Purple (+ 40 seconds)
    * 4 - AA = Rush Hour, White (ish) (+ 45 seconds)
    
* Game Reset: Restarts the the current game mode and apply the difficulty switches.

* TV Type (Color / BW): Changes between the default background color and a black background. A completely black background offers better contrast and might work better on Black and White televisions, but can be hard on the eyes. The main reason for this feature is to provide accessibility for people with color blindness or other disabilities. This can be changed anytime during gameplay.

* Game Select: Changes the game mode, this must be done before starting the game (or after a reset) while the title is displayed. The game mode is in the top left corner:
    * Mode 0 = Default mode, traffic level changes every checkpoint, and keep cycling. The difficulty switches define only the starting traffic intensity.
    * Mode 1 = Similar to Mode 0, but the traffic level defined by the switches does not change.
    * Mode 2 = Mode 0 + Randomized traffic lines.
    * Mode 3 = Mode 1 + Randomized traffic lines.
    * Mode 4 = Mode 0 + Bigger speed difference between traffic lines.
    * Mode 5 = Mode 1 + Bigger speed difference between traffic lines.
    * Mode 6 = Mode 2 + Bigger speed difference between traffic lines.
    * Mode 7 = Mode 3 + Bigger speed difference between traffic lines.
    * Mode 8 = Mode 0 + Random traffic intensity every checkpoint.
    * Mode 9 = Mode 1 + Random traffic intensity every checkpoint. 
    * Mode A = Mode 2 + Random traffic intensity every checkpoint.
    * Mode B = Mode 3 + Random traffic intensity every checkpoint.
    * Mode C = Mode 4 + Random traffic intensity every checkpoint.
    * Mode D = Mode 5 + Random traffic intensity every checkpoint. 
    * Mode E = Mode 6 + Random traffic intensity every checkpoint.
    * Mode F = Mode 7 + Random traffic intensity every checkpoint.

Mode 0 tries to offer the most balanced experience.

Bigger speed difference between traffic lines makes the game a little harder, with opportunities for overtaking opening and closing much faster and changing lines is more difficult. 

For modes 8 to F, the traffic level to be cyclic or fixed only has effect on the checkpoint time. In this mode, locking into rush hour for example, will make the game easier, since you will always get 45 seconds.

It much easier to read it as a binary number (like linux file permissions). Each byte defines a property (0 / 1).

* D0 => (Cyclic / Fixed) traffic intensity.
* D1 => (Constant / Randomized) traffic lines.
* D2 => (Smaller / Bigger) speed difference between lines.
* D3 => (Constant / Random) traffic intensity.

Deterministic game modes (0,1,4,5) will always generate the same sequence of cars for each line.

## Border Effects

While in the title screen it is possible to change what the border of the screen looks like by pressing the D-pad:
* Up (default) => Basic strip pattern.
* Left => Tachometer, the stripes grow representing the engine RPM, the vertical line position represents the current gear.
* Down => Vertical parallax, the planes are on top of each other
* Right => Horizontal Parallax, the planes are next to each other.

 
## Controls
* The button starts the game and accelerates.
* Up also accelerates, down breaks, and you can move left to right.
* It is possible to break and accelerate at the same time, this will break with half intensity (Heel-and-toe).

## Closing Thoughts
A very special thanks to all the AtariAge community. You can get the most recent updates about Hellway in https://atariage.com/forums/topic/316402-hellway-an-atari-2600-homebrew-with-love/

