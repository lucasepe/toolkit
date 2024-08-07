# `wactl`

Send bulk WhatsApp ad messages using your Android device an your PC via Android Debug Bridge (adb).

The wactl utility sends custom WhatsApp messages to your contacts.

Just provide a CSV file with your contacts and a TXT file with 
your message template. You can also send images!

PREREQUISITES

 * An Android device with "Developer Options" enabled and with
   WhatsApp installed
 * A PC with Android Debug Bridge (adb) installed

wactl depends on the Android Debug Bridge (adb) tool that is the 
officially provided way of interacting with android devices via
terminal from desktops and laptops.

Refer to the [HOWTO](HOWTO_en.md) file on instructions about how to enable
the Android Developer options on your phone and how to install 
Android Debug Bridge (adb) on your desktop and laptop.

Refer to the [DOWNLOAD](DOWNLOAD.md) file for the links to download binaries 
for your OS Arch.

In order to specify the unlock screen PIN you have two options:

 * set the WACTL_PIN environment variable
 * use the -pin=XXX flag each time


If you find this tool useful, please consider making a donation:

  * https://www.paypal.com/donate?hosted_button_id=WSXXQ36U37FMJ

Your support motivates me to continue developing and improving this software.

Upon making a donation, please send me an email with your "app key," and I will 
generate and send you a license file that unlocks all features.

Once you have this file, put it in the same folder of the `wactl` executable.
