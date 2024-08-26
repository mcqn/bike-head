# Bike Head

Making your bike more fun (if that's possible) by giving it a head.

A laser-cut template to make a cardboard head to mount on the handlebars of your bike.  Then customize it with craft supplies or LEDs and a Microbit.

## Notes on creating the design

In FreeCAD...

1. Created a sketch of the side profile
1. Made a copy of that sketch
1. Opened the attachment editor for each sketch and offset one by 75mm on Z and -8&deg; rotation around Y, and the other by -75 and 8&deg;
1. Then in the Surface workbench, filled in each side to give two surfaces
1. And then repeatedly used the boundary curve to create each connecting surface between the sides
1. In the Draft workbench I selected all the centre, connecting surfaces and upgraded them to a shell
1. Then in the Mesh workbench I could convert the shell to a mesh and then unwrap it to get the net for those shapes
1. The convert to mesh and unwrap process was repeated for the two sides
1. Then used Transform to orient the sides to broadly the right place
1. And in the Draft workbench rotated and moved the sides to be offset by 3mm from the long face
   1. Selected each end of the corresponding lines in the side and the centre piece which are to be lined up, and noted their `x` and `y` coordinates.
   1. Worked out the angle of the centre piece line with respect to `y` (in this instance) - `theta`, with `tan^-1(x_diff/y_diff)`
   1. Worked out new coordinates for corresponding point in the side with `x_offset` being `3 * sin(90-theta)` and `y_offset` being `3* cos(90-theta)`
   1. Work out the distance to move the side so it ends up at the right place.  Use the Placement in the side's properties to nudge it
   1. Rotate the side to line up parallel to the corresponding line in the centre.  I ended up eyeballing this rather than calculating it
   1. Repeat for the other side



## Game Notes

### Pacman

### Tick

1. Start up and loop until someone is chosen or a timeout happens:
   1. Transmit your ID
   1. Wait to receive someone-else's ID
   1. Vote on who should be `it`?
1. If it was a timeout, assume someone else is `it` and proceed


1. To begin with, use a button press to select someone as `it`
1. Loop:
   1. If I'm `it`:
      1. Light LED
      1. Broadcast our ID
      1. Listen for a broadcast
      1. If a request to be `it` is received, send a confirmation of passing on
   1. If not `it`:
      1. Turn off LED
      1. Listen for a broadcast
      1. If one found, reply with a request to be `it`
      1. If it's a confirmation of `it`, you're `it`, count down from 5 before looping round



