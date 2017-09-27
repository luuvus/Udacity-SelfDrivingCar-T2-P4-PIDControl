# CarND-Controls-PID
Self-Driving Car Engineer Nanodegree Program

---
This project implements a PID control in C++ to drive a vehicle autonomously at highest speed possible in a computer simulated environment. In addition to driving at highest speed, the program needs to pick an optimal parameters to make the vehicle drive in as straight as posible, which mean minimal sway/swirl left and right.

The program/application receive vehicle's Cross Track Error(CTE), which is the distance between the lane center and the position of thevehicle, and use this error to calculate the values for Proportional, Integral, Derivative (PID). In the end, the program will calculate combine PID error value, which will be sent back to the vehicle as throttle/speed signal.

'P' is the proportional term affect the steering base on the Cross Track Error (CTE), which mean if the vehicle is facing toward the right of the lane, the 'P' value will adjust left, and vice versa.

'I' is integral term that track and calculate a sum of all observed CTE errors, which help the vehicle adjust to drifting issues, such as the vehicle is consistently drifting to the right of the lane, then it will adjust to back left. 

The derivative term 'D' evaluate the change in error between the previous error and current error to adjust overshooting of vehicle steering direction and bring the vehicle closer to the reference line.

A manual process was used in selecting value for PID parameters. Initially, I set various values for 'P', while setting zero for 'I' and 'D', and observe the result. This single parameter value setting method is applied to 'I' and 'D' until the vehicle begin to navigate within the lane. All paramereter values are started out at high value and slowly reduced until the vehicle achieve the desire high speed and minimal sway/swirl.

The final values of P, I, and D are set at 0.2, 0.0004, 4.0, which make the vehicle  achieve an average speed of 52 mph.

---

## Dependencies

* cmake >= 3.5
 * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1(mac, linux), 3.81(Windows)
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools]((https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)
* [uWebSockets](https://github.com/uWebSockets/uWebSockets)
  * Run either `./install-mac.sh` or `./install-ubuntu.sh`.
  * If you install from source, checkout to commit `e94b6e1`, i.e.
    ```
    git clone https://github.com/uWebSockets/uWebSockets 
    cd uWebSockets
    git checkout e94b6e1
    ```
    Some function signatures have changed in v0.14.x. See [this PR](https://github.com/udacity/CarND-MPC-Project/pull/3) for more details.
* Simulator. You can download these from the [project intro page](https://github.com/udacity/self-driving-car-sim/releases) in the classroom.

There's an experimental patch for windows in this [PR](https://github.com/udacity/CarND-PID-Control-Project/pull/3)

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./pid`. 

Tips for setting up your environment can be found [here](https://classroom.udacity.com/nanodegrees/nd013/parts/40f38239-66b6-46ec-ae68-03afd8a601c8/modules/0949fca6-b379-42af-a919-ee50aa304e6a/lessons/f758c44c-5e40-4e01-93b5-1a82aa4e044f/concepts/23d376c7-0195-4276-bdf0-e02f1f3c665d)

## Editor Settings

We've purposefully kept editor configuration files out of this repo in order to
keep it as simple and environment agnostic as possible. However, we recommend
using the following settings:

* indent using spaces
* set tab width to 2 spaces (keeps the matrices in source code aligned)

## Code Style

Please (do your best to) stick to [Google's C++ style guide](https://google.github.io/styleguide/cppguide.html).
