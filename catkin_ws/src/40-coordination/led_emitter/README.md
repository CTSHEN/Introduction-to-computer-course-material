# Package `led_emitter` {#led_emitter}

The coordination team will use 3 signals: CAR_SIGNAL_A, CAR_SIGNAL_B, CAR_SIGNAL_C.
To test the LED emitter with your joystick, run the following command:

    $ roslaunch led_joy_mapper led_joy_with_led_emitter_test.launch veh:=![robot name]

This launches the joy controller, the mapper controller, and the led emitter nodes. You should not need to run anything external for this to work. Use the joystick buttons A, B and C to change your duckiebot’s LED’s blinking frequency.

Button A broadcasts signal CAR_SIGNAL_A (2.8hz), button B broadcasts signal CAR_SIGNAL_B (4.1hz), and button CAR_SIGNAL_C (Y on the controller) broadcasts signal C(5hz).The LB button will make the LEDs all white, the RB button will make some LEDs blue and some LEDs green, and the logitek button (middle button) will make the LEDs all red

Repeat this for each vehicle at the intersection that you wish to be blinking. Use previous command replacing `![robot name]` the names of the vehicles and try command different blinking patterns on different duckiebots.

(optional tests) For a grasp of the low level LED emitter, run:

    $ roslaunch led_emitter led_emitter_node.launch veh:=![robot name]

You can then publish to the topic manually by running the following command in another screen on the duckiebot:

    $ rostopic pub /![robot name]/led_emitter_node/change_to_state std_msgs/Float32 ![float-value]

Where `![float-value]` is the desired blinking frequency, e.g. 1.0, .5, 3.0, etc. If you wish to run the LED emitter test, run the following:

    $ roslaunch led_emitter led_emitter_node_test.launch veh:=![robot name]

This will cycle through frequencies of 3.0hz, 3.5hz, and 4hz every 5 seconds. Once done, kill everything and make sure you have joystick control as described above.