How To Quadcopter
=================

The main purpose of this guide is to impart knowledge I've gained building and programming a Quadcopter that if I could go back in time I would tell myself at the beginning. By reading this guide, you'll get an idea of what to avoid, how to go about, and the tasks involved in building and programming a Quadcopter.

This guide is for people who want to build and program their own Quadcopter. I mean, who wouldn't? However, if you just want to buy one, or buy a flight controller, there are probably better guides elsewhere. But you should still read this ;).

Table of Contents:

 * [Terminology](#terminology)
 * [Parts](#parts)
 * [Flight Mechanics](#flight-mechanics)
 * [What Not to Do](#what-not-to-do).

## Terminology

 * Electrical units

Electricity is the flow of electrons. This can be confusing, but basically you have Volts (V), Amps (A), and Watts (W or P). Volts is a potential difference; think of it like a power multiplier. Amps is the amount of current, which is basically the rate of flow of electrons. Watts is the amount of power, which is _Amps * Volts_. You might also see Coulombs (C), which represents the number of electrons (in some [random float]*10^[big number] unit). Amp Hours (Ah) represents the amount of amperes that can be sustained for one hour, which measures capacity.

## Parts

Essential Parts:

 * Motors

Motors are what propel your board. You'll need four of them. The motors on a Quadcopter are brushless, which basically mean they only spin one way and are more efficient and durable than a typical motor. You might hear them referred to as stepper motors. A brushless motor has three wires which are stranded, with each strand leading to a coil. To power the motor, the ESC sends positive to one wire and negative to another in rapid sequence.

 * ESCs

Controlling a motor is actually rather difficult to do manually. Electronic Speed Controllers do all the work for you. They have two wires (power and ground) that you can hook up directly to a battery. There's also a control cable with three wires: Signal, BEC/5V, and Ground. Signal is typically yellow/white, BEC/5V is red (and usually in the middle), and ground is black/brown. You don't need to connect the middle cable. Hook up the ground somewhere (is this necessary?), and hook up the signal to a PWM pin (or any IO pin) on your flight controller. Quick heads up: ESC PWM signals are pretty much always on a 20hz (50ms) cycle with 1ms to 2ms high time for power, with a startup sequence of 1-5 seconds on lowest power.

 * Battery

You pretty much want to use a Lipo (Lithium Polymer) battery. Generally batteries have a handful of values, but the three big ones are voltage/number of cells, capacity, and discharge rate. Voltage is usually determined by the number of cells, with each cell usually providing 3-4V (double check). Cells are given in S, so a 3S battery has three cells and usually has 12V (usually written as 11.1V). Capacity is given in milliamp hours (mAH), or how many milliamps it can supply for an hour.

 * Flight Control Board

You can either buy a board as a product, which is the easier solution (for the lazy n00bs), or you can use firmware for an Arduino (for the slightly less lazy noobs), or you can program your own firmware. If you use an Arduino, you'll have access to lots of support and libraries (not fun). Or you can use a different board (like a Parallax Propeller) and program it all yourself from scratch (for hardcore hardware hackers). Your choice really. A flight control board is responsible for controlling all the aspects of your quadcopter; such as sensors, radio transmitters, and any other devices you have; and stabilize the quadcopter by changing the output to all the motors.

 * IMU (Inertial Measurement Unit) (Accelerometer + Gyroscope)

This device is essential for stabilization of your Quadcopter. One thing you may or may not be aware of is that you'll use both an accelerometer and gyroscope to calculate just two axis: Pitch and Roll. Though you can estimate yaw, if you want to be able to maintain a steady heading or turn precisely you'll need a IMU with a magnetometer as well. The gyroscope measures angular acceleration (how fast speeding up or slowing down in rotation). However, it doesn't always reset to zero, so when you try to find your angular velocity, it will drift over time. The drift can be compensated for by the accelerometer, which measures pitch and roll values by taking the value of gravity read on all three axis (An accelerometer is essentially a ball on a spring, which is how it can measure gravity). However, the accelerometer is not very accurate, and vibrations or movement can cause spikes in the data. By combining the drifting gyroscope data with the uneven accelerometer data through a Kalman or Complementary filter, you can get accurate headings.

## Flight Mechanics

 * How does a quadcopter fly?

A quadcopter has four motors... [finish later].

## What Not to Do

Here's a small list of things not to do:

 * Strip motor wires.

With a brushless motor, each of the three wires has a bunch of strands. Each of those strands leads to its own coil, so their all individually insulated. At the end, there's no insulation, and the strands are twisted together. If you cut it, you leave your motor pretty much useless.

 * Reverse polarity to the board.

You'll fry the board.

 * Reverse polarity to the ESC's.

Take a guess-- You'll fry the ESC. It will sparkle and smoke. If you're thinking "OOH FIREWORKS" unplug it.

 * Use crimp connectors or other modular wiring components.

It might seem easier to use crimp connectors for wiring. It's not. Just solder everything. If something goes wrong, desolder it and replace it. It's actually a lot easier than using crimp connectors. They also make it a pain to wire stuff.

 * Cut wires too short.

"Measure twice, cut once." Here it's think twice, buy replacement parts never. Nothing sucks more than buying replacements for perfectly functioning components.

 * Don't fry your board.

It's a lot easier than it sounds. Simply grounding pins can destroy your board. Read [10 Ways to Destroy an Arduino](http://www.ruggedcircuits.com/10-ways-to-destroy-an-arduino/).
