# The Knob Problem

It's not trivial to implement a knob widget. The correct behavior is: beyond +90% and above -90% it should stuck at +90% or -90%, respectively.

This little toy demonstrates the solution. The gray upper field shows the naive value.

Known issue: in stuck state, if the user goes back to zero position, it jumps to it. But maybe it's okay.
