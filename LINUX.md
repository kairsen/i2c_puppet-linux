# I2C Puppet mods for Linux systems

The original version lacked certain characters, such as  <ESCAPE>, and the characters "<>{}[]^&%=\"
which made it difficult to use on Linux systems
    

This version of the firmware has been modified to support Linux systems.
The following changes have been made
    1) The backspace key works during the GUI login
    2) The Sym key not acts as a Control key, so SYM+C is Control-C
    3) The four top button keys are now used to provide the missing characters.

The original definiton of the keys were this 

	    L1	    L2		R1		R2		SPKR	Mic BS  NL  SPACE
		                            	$		~   \b  \n
Shift  
Alt	                                            0
Sym		                                                |	TAB



The current definition of the keys are

        L1      L2      R1      R2      SPKR    Mic BS  NL  Spacebar
<none>  <esc>   %       =       \       $       ~   BS  \n  <space>
Alt     >       ]       }       &       `       ~   x       <tab>
Shift   <       [       {       ^       $       `   BS      <space>
Sym     x       x       x       x       $       ~   BS  |   <space>


#Linux Debug tips

The keyboard was two "outputs" - one is the USB HID interface, the other is the serial port.
Any printf() command goes to the serial port.

When the keyboard is plugged into a Linux system, a new TTY interface will appear. I usually use "ls -lt /dev/tty* | head"
to learn the name, as the newest port will appear first. On my system, it's /dev/ttyACM0

So on one terminal, I type

cat -v </dev/ttyACM0

while on a second terminal window, I type

cat -v

The first one will print all of the printf output, and the second will show you how the keyboard works normally.

#Compiling on Linux

I edit the files in <GIT>/ic2_puppet/all/ using my preferred editor. In my case, I use emacs. I have the keystroke combination "Control-C M" bound to compile, using 

(global-set-key "\C-cm" 'compile)

And when I press these keys, emacs saves all files, and recompiles the
code. I have a small hub with switchable on/off ports, and restart the
keyboard into boot mode, and then do a "make install" to load the new
firmware


#TODO

Currently - the SYM+Button keys are defined as the character "x" to indicate it's not been specified.
I'l like to make these keys to the 4 arrow keys.

Also - it might be possible to create key combinations by combining the modified keys, like SYM+Alt+key
