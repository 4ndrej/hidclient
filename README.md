# hidclient

Virtual Bluetooth® keyboard and mouse

## What is this about?

The hidclient program makes a Bluetooth® technology equipped computer appear as a Bluetooth® keyboard and mouse device to other machines. Input events (like keystrokes and mouse movements) of the locally attached input devices will be forwarded to another machine via the Bluetooth® link.

For the counterpart (which might be a Linux PC, a Win PC, a PDA...) there is no technical difference to "real" Bluetooth® input devices.

## What will I need?

* A Linux PC (or laptop, possibly a PDA would do...?) that runs the Bluez Software. Most distributions should supply this.
* A Bluetooth® dongle (USB-Stick...) for this machine
* Another device that is able to handle Bluetooth® input devices: A PC, PDA or similar (not necessarily running Linux!)
* The bluez header files (for compiling the sources)
* The hidclient source code (see below).


## How to?

* Dowload and uncompress hidclient files:
    tar -xjf hidclient-20060725.tar.bz2

* Compile program, copy other files to the correct places:

    make
    cp hidclient /usr/local/bin
    cp hid-sdp-record.bin /etc/bluetooth/

* Make sure that no HID daemon is running:

    killall hidd

Both hidclient and hidd regularly use the same "port" (PSM), thus you need to stop hidd first. It is not the specification that requires the imperative usage of the same port number, but there are devices that refuse to communicate over non-standard PSM. There also was a version of a Windows-stack that would not work with alternative PSM numbers.

* Change to a text console (optional) by pressing Ctrl+Alt+F1 (...F6)
On those text-only consoles stray input events will do the least harm: While running hidclient the Linux machine will also receive the mouse and keyboard events while forwarding them.
* Start hidclient

    /usr/local/bin/hidclient

You should get a list of event-devices that hidclient will accept input events from, along with a notice that hidclient waits for an incoming connection.
* Activate a "device search" on the other machine - it should detect the virtual keyboard. Use the regular mechanism for connection the remote machine to the hidclient PC - this should also give a "connection" message on the hidclient machine.
* Press keys, move the mouse: This should yield reaction on the remote machine.
* To disconnect (from the hidclient side) press the "Pause" key on the keyboard (might be labelled "Interrupt" instead). This is the means for cleanly shutting down the connection.
To stop hidclient at the same time you can also use the key combination LeftCtrl+LeftAlt+Pause.

## Where to get the necessary files?

Here:

* hidclient-2006-0725.tar.bz2 - Archive including all necessary files
* hid-sdp-record.bin - The (binary) descriptor for the virtual device
* hidrecord.txt - The textual explanation of that descriptor
* hidclient.c - The source code proper

## What am I allowed to do with this program?

Well, you may use it, read the source code, give the files to other people, change it - basically anything provided you stay within the limits of the GNU General Public License version 2 (or any later version, at your choice).

This program is "free software" (both as in speech and in beer), you do not need to pay any royalties for using it. Keep with the GPL.

