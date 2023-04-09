# Welcome

This is a repo where I play with my debuggers.

Here are some commands that I have found helpful for these tools:

# GDB

to jump through loops quickly just set a breakpoint after the loop and then type continue to get there.
use the tui.
gdb program
start -> runs until program til start of main. useful
info locals
p 7+8 yields 15.


command | shortcut | description | usage
next | n | steps forward into the code. executes the entire function if the next statement is a function call. (see dichotomy with step) |
step | s | steps forward one instruction. if the next line is a function call it steps once into the function call. |
break | b | code execution stops at the breakpoint set. | b main or b main.c:XX
backtrace | bt | | 
list | l | |

info gdb  					//Manual
info locals 				//Vars in local scope
info variables				//Vars declared outside current scope
info functions				//Names and datatypes of all defined functions
info b 						//List all breakpoints
break funcName				//Set breakpoint at function funcName (short: b funcName)
break file::line			        //Set breakpoint at line in file
layout next					//Cycle through the layouts of gdb
p var 						//Print the value of variable var
p var = value 			        	//Force set value to a var
run 						        //Start the program
start 						//Synonymous to (b main && run). Puts temporary b at main
next 						//Execute the current line in source (short: n)
step 						//Step into function call at current line (short: s)
finish						//Finish the execution of current function (short: fin)
continue					//Resume execution (After a breakpoint) (short: c)
refresh 					        //Repaint the interface (To fix corrupted interface)
shell cmd 					//Run shell command cmd from gdb prompt
python gdb.execute(cmd)		//Run a gdb command cmd from python prompt
set print pretty on			//Enable pretty printing
							  (Put in ~/.gdbinit)
$ gdb -c core.num			//Examine the dumped core file from a SIGSEGV(shell command)
bt							//Print backtrace
break _exit 				        //Breakpoint at exit of program
whatis expr					//Print datatype of expr
ptype expr					//Detailed print of datatype of expr
watch var 					//Stop when var is modified
watch -l foo				        //Watch foo loaction
rwatch foo					//Stop when foo is read
watch foo if foo>10			//Watch foo conditionally
delete						//Delete all breakpoints
delete breakpoint_no		        //Delete breakpoint breakpoint_no
command breakpoint_no		//Run user listed commands when breakpoint is hit
							  (End list of commands with 'end')
file executable 			        //Load the executable for debugging from inside gdb
quit						        //Quit (short: q)

## TUI

This is OP. Use it

layout [option]
options:
    asm: assembly window only
    next: next
    prev: previous
    regs: register window

## Core Dumps

ulimit -c unlimited
echo "./core" > /proc/sys/kernel/core_pattern

# LLDB
