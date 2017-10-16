# multikey_teleop

## Overview

*multikey_teleop* is a node for robot teleoperation.
It uses keyboard to produce *Twist* messages.
It's basically a keylogger, listening on any key press and producing commands accordingly.
Its main advantage is that you will be able to simultaneously press multiple keys.
An other advantage is that it will work even if your terminal doesn't have the focus.

## Quickstart

Execute the following command to control a turtle with *multikey_teleop*.

    roslaunch multikey_teleop turtle.launch

Press *WASD* or arrow keys to move the turtle.
Press *Escape* to disable command and press it again to enable it back.
Press the *Left Shift* key to go faster.
Press *Space* to brake.

## Node

### multikey_teleop

#### Published topics

cmd_vel (geometry_msgs/Twist)
: velocity command

brake (std_msgs/Bool)
: publish True if brakes should be on

#### Parameters

~linear_speed (double, default: 1.0)
: the forward/backward speed [m/s]

~angular_speed (double, default: 1.0)
: the rotation speed [rad/s]

~speed_factor (double, default: 1.5)
: the multiplicative factor applied to linear and angular speed when FAST key is pressed

~rate (double, default: 10.0)
: the command publication rate [Hz]

~publish_null (double, default: False)
: if true, will publish null commands when no key is pressed

~should_hide_inputs (double, default: True)
: if true, will hide key press in terminal where launched

~key_map (struct, default: see below)
: assign keys to actions

##### Key Map

Here is an example of key map configuration.

    forward: [w, up]
    backward: [s, down]
    left: [a, left]
    right: [d, right]
    brake: [space]
    pause: [escape]
    fast: [shift_l]

Each line represents an action and for each action is assigned a set of keys which will trigger the corresponding action when pressed.
