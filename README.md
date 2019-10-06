# MULTIPOSITION-SERVO
A modular water treatment system is being integrated into an existing system.  When the host system 
calls for a cycle, our servo will cycle a control valve from the home position to fill for 10 seconds, then to 
drain for 20 seconds, then to flush for 10 seconds, and then back to home until the next call.  The cam‐
operated microswitches tell us what position the valve is in. 
BONUS TASK 1: If you really want to show off, create an integer N7:0 which reports the current position 
of the valve.  The positions should be 0 = HOME, 1 = FILL, 2 = DRAIN, 3 = FLUSH and 4 = TRAVELLING 
(between positions). 
BONUS TASK 2: Set up B3:0/0 as a reset / interrupt button which will abort the process and return the 
valve to the home position. 
## IO / ASSIGNED MEMORY
I:0/0 ‐ Home microswitch (closes when valve in home position), 
I:0/1 ‐ Fill microswitch (closes when valve in fill position) ,
I:0/2 ‐ Drain microswitch (closes when valve in drain position),
I:0/3 ‐ Flush microswitch (closes when valve in flush position),
I:0/4 ‐ Cycle call (signal closes when host requires a cycle) ,
O:0/0 – Servo (energize to turn the cam thus changing valve position), 
Bonus IO: 
N7:0 – Valve position integer, 
B3:0/0 – Reset / cycle interrupt button. 
### TEST CRITERIA
To start, run your program on Emulate.  The servo should energize immediately.  If you did the bonus 
portion of this project, N7:0 should be equal to 4. 
Next, force the fill microswitch on (closed).  The servo should still remain energized looking for home, 
but N7:0 should now be 1. 
Third, force the fill microswitch back off and the home microswitch on.  Now the servo should 
deenergize and N7:0 should be set to 0. 
Fourth, momentarily force I:0/4 on and then back off.  The servo should energize once more, but N7:0 
should still be 0. 
Next step, force the home microswitch off.  N7:0 should go to 4.  Then force the fill microswitch on.  
N7:0 should be equal to 1 and the servo should deenergize FOR ONLY 10 SECONDS and then start back 
up automatically. 
Now, force the fill microswitch off.  N7:0 should go to 4.  Then force the drain microswitch on.  N7:0 
should be equal to 2 and the servo should deenergize FOR ONLY 20 SECONDS and then start back up 
automatically. 
Only one more mode to test.  Force the drain microswitch off.  N7:0 should go to 4.  Then force the flush 
microswitch on.  N7:0 should be equal to 3 and the servo should deenergize FOR ONLY 10 SECONDS and 
then start back up automatically. 
Finally, force the flush microswitch off.  N7:0 should go to 4.  Then force the home microswitch on.  N7:0 
should be equal to 0 and the servo should deenergize and stay that way.  SUCCESS! 
Bonus test: momentarily force I:0/4 on and then back off.  The servo should energize, but N7:0 should 
still be 0.  Then toggle B3:0/0 on and then back off.  Next, force the home microswitch off and the fill 
microswitch on (closed).  The servo should still remain energized looking for home, but N7:0 should now 
be 1.  To wrap it up, force the fill microswitch off.  N7:0 should go to 4.  Then force the home 
microswitch on.  N7:0 should be equal to 0 and the servo should deenergize and stay that way. 
