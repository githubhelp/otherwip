#### Configure the Serial UART

By default the Raspberry Pi has it's external serial UART configured to monitor debug information via a terminal, this configuration should be changed to provide access to the "serial port".

To do this 2 files need to be edited (unless previously done).

     sudo nano /etc/inittab 

Locate this line in the file (it's usually the last line)

    # T0:23:respawn:/sbin/getty-LttyAMA0115200vt100

By default the hashtag (#) will not be present, this line should be *commented out* by adding the hashtag at the begining of the line if absent, the line needs to be as shown, **with** the hashtag. exit using ` ctrl-x ` saving any edits with ` y ` and ` enter `.

    sudo nano /boot/cmdline.txt

If the one line in this file contains this block of text 

    console=ttyAMA0,115200kgdboc=ttyAMA0,115200

it should be deleted, leaving the remaining text as one line, exit using ` ctrl-x ` saving any edits with ` y ` and ` enter `.

*Note - the changes will take effect at the next restart* 

-----------------------------------------------------------------------------------------------------
