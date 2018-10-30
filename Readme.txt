
This is the starting point for the Mila work for Princeton (among other software needed for this development cycle).

Starting point is the Mila PC UI.
Note: when changing project settings (talking about binary to text formatted projects - in binary everything is stuffed
into a file that is the project, in text all elements of a project are saved in their own files (modules, globals, dialogs etc)
which is how you really want things and need things in a software configuration environment). 

AutomatedHybrid - 1) Princeton is what should be called an automated system (program it and it should just run and run and run...)
                  2) Although not a true Mila system, it uses the Mila commands
                  3) Stepper motor control: intended on using StepUp, decision was to scrap StepUp and interface with the
                     AMS controller directly since we want a system to run "forever", just keep the stepper motor
                     running at some speed until a run is done
                  4) TBD  

Here the idea is to create a standalone Mila instruction set as an importable/exportable module as well as any related
functionality (globals, etc). This way as Mila-based interfaces come along there's a common set of functionality that
can be shared.

This also means using text/xml for project and code saves. This makes it easier to save some development as export/import
modules as (or if) these come along.

9/30/15

Took out commPort (Mila window) and all references (global properties) to old MIla serial port, it's popup index, name etc.
and replaced all that with a set of arrays of length NumberOfCommPorts for the serial port indices (popup selction), serial objects,
as well as the baud, data bits, parity and stop bits (anything dealing with the serial ports, parameter settings etc).

10/5/15

Added a configuration file reader to allow for configuring the stepper motor controller (the settings are reflected in the
AutomatedHybrid UI but are not changable the in UI). See PossibleProblems.txt - pain in the ass with reading text files (so far)
is that debugging generates a MyDebuggingLog folder during debugging and then removes it on termination so there's no way for the
text file to be resident in the executable folder!!