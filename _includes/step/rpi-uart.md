#### Configure the Serial UART

By default the Raspberry Pi has it's external serial UART configured to monitor debug information via a terminal, to provide access to the "serial port", this configuration can and should be changed .

To do this 2 files need to be edited (unless previously done).

     sudo nano /etc/inittab 

Locate this line in the file (it's usually the last line)

    # T0:23:respawn:/sbin/getty-LttyAMA0115200vt100

By default the hashtag (#) will not be present, this line should be *commented out* by adding the hashtag at the begining of the line if absent, the line needs to be as shown, **with** the hashtag. exit using `ctrl-x` saving any edits with `y` -> `enter`.

    sudo nano /boot/cmdline.txt

This file contains one line, check to see if it contains this block of text,  

    console=ttyAMA0,115200kgdboc=ttyAMA0,115200

It should be removed leaving the remaining text as one line, exit using `ctrl-x` saving any edits with `y` -> `enter`.

*Note - the changes will take effect at the next restart* 

-----------------------------------------------------------------------------------------------------
