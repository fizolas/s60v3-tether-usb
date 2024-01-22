# s60v3-tether-usb
USB tethering of s60v3 phone in Debian 12 (bookworm) 

Tethering means sharing the internet connection in your phone with your computer 

Put wvdial.conf in /etc, or include it into an existing /etc/wvdial.conf, and replace "data.provider.com" with the IP of your own internet provider (complete Username and Pasword, if needed)

Put the s60v3-tether-usb script in ~/bin or some other directory in the path, and make it executable (chmod +x s60v3-tether)

Put yourself in the sudoers group: e.g. for user john: "usermod -aG sudo john" (for this to be effective you need to log out and log in again)

Connect the phone to the computer with a suitable USB cable (warning: not all cables work) and put the phone in "PC Suite" mode (NOT: in "Connect PC to web" mode.

Run "s60v3-tether-usb" in a terminal to tether the phone,

Ctrl-C stops the tethering session leaving the system consistent (both during dial-up channel search or during wvdial)

Tethering works well with Nokia E52, but it shoud work with other phones too.

Note 1: default device for connection is /dev/ttyACM0. It this does not work, disconnect phone type "sudo udevadm monitor --udev" and reconnect phone (choosing "PC Suite" mode): look
for the correct /dev/tty*** device and replace it in /etc/wvdial.conf

Note 2: for the Evolution email client to work during tethering, set "Method to detect online state" to "base" in "Settings>Network Preferences" 
