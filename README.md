# Soduko
an algorithm to solve any soduko puzzle 

The algorithm holds a pointer that run along the table. 
For every iter it up the value of the cuurent blank by 1 and check it's validity according to the soduko rules. 
If it gets to a pointer that it can no longer increase the value (reached 9) it clears it and goes back the the last blank.
in additional, it holds an array called Fixed numbers, that its job is to alert which numbers where given and can not be changed.
