# Mario-Kart Inspired Racing Game Final Project

## Project Introduction

## High Level Design

The inspiration for our project came from the game Mario Kart Wii. The core structure of a Mario Kart game consists of a player vehicle, the track, a lap counter, and a motion controller. We took these core ideas and did our best to implement them using the PICO and VGA screen. 

The logic of our game follows a straightforward set of directions. Once the game begins, if the car ever intersects with a track boundary, the game ends. Also, if it ever encounters a marker, increase the scrolling speed and increment the score counter. This continues until the player causes a game over or if the player reaches a score of 20. After a game over, the player has the option of resetting by hitting the reset button, score is reset and a new map is generated. 

The only copyrights that are relevant to our project concern the use of Spotify and using the app to play music. We registered the app through the online platform for app developers, so sharing videos of the app and the songs playing is acceptable. 

#### Hardware/Software Trade-Offs

From a general perspective, the choice was made early on to make the project more logic and software dependent rather than hardware dependent. This involved only utilizing the minimal amount of hardware necessary to aid the movement of the car and collisions with the marker and road. As such, the only hardware components utilized were the VGA screen, IMU, and a vibration motor. 
 
Since our initial plan included a sound and music component, the spotify route as opposed to the sound synthesis was chosen. The spotify route allowed including a larger dataset of songs and significantly reduced computational overhead. However, spotify did limit the ability to customize the music at each marker collision. We played a cool synthwave playlist that fit the vibes of our game. Ultimately, the ease of implementation, reduced computation, and reduced hardware (DAC is not necessary) made spotify the better option over the digital synthesis route.
 
Lastly, for the marker collision, a decision was made to only count the collision if the car’s top line with any point of the marker. This significantly lowered the collision logic for markers within the main thread, but this also made hitting markers somewhat challenging. Ultimately, this simply became embedded into our game’s natural difficulty.


## Hardware Design

The hardware for our controller is straightforward and concise. All circuitry is done on a single breadboard and the wiring is neatly organized to avoid complications. Below we have detailed every component of the hardware as well as many diagrams and pictures of the circuitry.

1) Pico - Microcontroller in charge of running the game code, writing to the VGA screen, and taking input from the MPU-6050
2) VGA - Graphics screen that follows HSYNC and VSYNC protocol to display the track, car, and score.
3) Breadboard - 16.6 cm by 5.6 cm breadboard that holds all the hardware circuitry.
4) MPU_6050 - Gyroscope sensor attached to controller in order to measure acceleration and tilt angle. Data is used to move the vehicle on screen accordingly.
5) Vibration Motor - Used to send vibration feedback whenever the player hits a marker. Controlled using PWM. 
6) 2N3904 NPN - The transistor used in the vibration motor circuitry. Allows for better control of the motor.
7) Push Button - A simple button used to start a new game or restart after a game over. It is attached to the outside of the controller.
8) Cardboard Container - A cardboard rectangular prism, approximately 18 cm by 6 cm by 5 cm. All circuitry is encapsulated by the prism. There are holes on the side to allow wires from the VGA and laptop. Can be opened and closed to allow adjustments to the breadboard.



![image](connection_diagram.png)
*Figure 1: Overall Hardware Setup*

![image](vibration_motor.png)
*Figure 2: Vibration Motor Circuitry*



### High Level Software Design



