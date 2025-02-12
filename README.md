# The Knob Problem

## What

It's not trivial to implement a fixed range knob widget. The correct behavior is: beyond +90% and above -90% it should stuck at +90% or -90%, respectively, just as IRL knobs do.

## Why

A naive implementation is when the knob (and the value) follows the mouse pointer or touch position. In this case, the user can jump from the start of range to the end of range, which is not a correct behavior. The knob should stop at the end of ranges, and keep stuck even the user reach the opposite end of the range.

In case of a real knob, once the user got stuck, there is only one way to unstuck and set other values: by going back on the path. In mouse/touch GUI, when the knob is in stuck, the user still can continue grabbing the pointer, and go to any position. The big question is when the stuck state should end.

In current implementation, if the knob is stuck at -90% or +90%, the stuck state ends at -90%..-70% and +70%..+90%, respectively, avoid jumping from -90% to a distant position.

A perfect handling would be to check the direction of the move, and un-stuck only when the user got to the position by turned back on the path.

It has another issue: grabbing the knob at near to its center may lead to skip the dead zone (-90%..+90%). This should be eliminated by disabling the center of the knob.

## Show

This little example demonstrates the solution. The gray upper field shows the naive value.
