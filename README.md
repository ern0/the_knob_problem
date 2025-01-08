# The Knob Problem

## What

It's not trivial to implement a fixed range knob widget. The correct behavior is: beyond +90% and above -90% it should stuck at +90% or -90%, respectively, just as IRL knobs do.

## Why

A naive implementation is when the knob (and the value) follows the mouse pointer or touch position. In this case, the user can jump from the start of range to the end of range, which is not a correct behavior. The knob should stop at the end of ranges, and keep stuck even the user reach the opposite end of the range.

In case of a real knob, once the user got stuck, there is only one way to unstuck and set other values: by going back on the path. In mouse/touch GUI, when the knob is in stuck, the user still can continue grabbing the pointer, and go to any position. The big question is when the the stuck state should end.

In current implementation, if the knob is stuck at -90% or +90%, the stuck state ends at -90%..0 and 0..+90%, respectively. Maybe these values should be -50%..0 and 0..50%, avoid jumping from -90% to 0 or +90% to 0.

A perfect handling would be to check the direction of the move, and un-stuck only when the user got to the position by turned back on the path.

## Show

This little example demonstrates the solution. The gray upper field shows the naive value.
