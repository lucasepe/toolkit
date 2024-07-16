# `wactl` (How to)

Enable Developer options on your phone
--------------------------------------------------------------------------

Your phone has several developer options that can be used by 
application developers for testing purposes. These options are 
typically hidden by manufacturers.

Follow these steps to enable the Developer options menu:

1. Go to "Settings" > "System"

2. Touch "About phone"

3. Then tap the "Build number" option seven times to enable Developer Mode.
   You will see a toast message when it is done.

4. Go back to the main "Settings" screen, and you should see a new 
   "Developer" options menu you can access.

5. Go in there and enable the USB debugging option

Now your phone is ready to communicate with your computer.

Installing Android Debug Bridge (adb)
--------------------------------------------------------------------------

wactl depends on the Android Debug Bridge (adb) tool that is the 
officially provided way of interacting with android devices via
terminal from desktops and laptops.

You can download the Android SDK Platform Tools for your OS here:

   https://developer.android.com/tools/releases/platform-tools

Extract the contents of this ZIP file into an easily accessible folder.
To access the adb tool from any directory all you need to do is adding
the adb directory to the PATH variable of your operating system.

Below are easier ways to install the tool on different operating systems.

MacOS:

If you are an  Homebrew (https://brew.sh/) user, the easiest way 
to install adb on MacOS is:

    brew install --cask android-platform-tools

Linux:

For Ubuntu/Debian:

    sudo apt install adb

For Fedora Linux:

    sudo dnf install android-tools

For Arch Linux:

    sudo pacman -S android-tools

Windows:

If you are a Chocolatey (https://chocolatey.org/install) user:

    choco install adb


The Contacts CSV file format
--------------------------------------------------------------------------

Each row in the CSV contacts file is composed of four fields:

    FirstName,LastName,BirthDate,MobileNumber

- BirthDate format is: ISO 8601 (https://en.wikipedia.org/wiki/ISO_8601)

    example: 8 January 1971 must be written as "1971-01-08"

- MobileNumber format is: E.164 (https://en.wikipedia.org/wiki/E.164)

    example: [+][country code][area code][subscriber number]


The Message TXT Template
--------------------------------------------------------------------------

Your message can eventually be 'templatized' by using placeholders and functions.

Example (a probable content of your 'promo.txt' file):

    Hi {{ .FirstName }}! 
    
    {{- $days := daysUntilNextBirthday .BirthDate -}}
    {{ if lt $days 6 }}

    In {{ $days }} days it's your birthday and 
    we thought of giving you a gift! 

    Here is a discount code: XXXXXX. 
    {{ end -}}

    There are many new things waiting for you in 
    our store, go check them out!

Explanation:

  This template is used to create a personalized message. It makes the message 
  special by including the person's first name and giving them a discount code 
  if their birthday is within the next 6 days. 
  
  Here's a breakdown of how it works:

    - The message starts by saying "Hi" followed by the person's first name. 
      The placeholder {{ .FirstName }} is used to insert the person's first 
      name into the message.
    
    - The template calculates how many days are left until the person's next birthday. 
      This calculation is done using the person's birth date. 
      The result is stored in a variable called $days.
    
    - The template checks if the person's birthday is within the next 6 days. 
      This is done using an "if" statement: {{ if lt $days 6 }}. If there are 
      fewer than 6 days left until the birthday, the next part of the message 
      is included.
    
    - If the condition is met (i.e., the birthday is within the next 6 days), the 
      message tells the person how many days are left until their birthday and 
      mentions that a gift is being given. 
      The exact number of days is inserted using the placeholder {{ $daysUntilBirthday }}.
    
  To summarize, this template personalizes a message with the recipient's 
  name, checks if their birthday is soon, and if it is, includes a special 
  birthday message and a discount code. 
  Otherwise, it simply invites the recipient to explore new items in the store.
