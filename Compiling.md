Compiling boblight on Ubuntu.

First step: install necessary dependencies:

sudo apt-get install libx11-dev libgl1-mesa-dev libxrender-dev libxext-dev portaudio19-dev libavcodec-dev libavformat-dev libswscale-dev libavdevice-dev

Second step: get the source:

> $ cd ~
> $ svn checkout http://boblight.googlecode.com/svn/trunk/ boblight-read-only

> $ cd boblight-read-only/
> $ ./configure

Third step: compile:
> $ cd boblight-read-only/
> > $ ./configure

> If everything goes well.....
> $ make
> $ sudo make install

Fourth step configure boblight for your controller:
> Depending on your controller you should move the correct config files to /etc
> under ~/boblight-read-only/arduino you will find config files for different setups.

> For a arduino duemilanove,
> > $ sudo cp ~/boblight-read-only/arduino/duemilanove.conf /etc/boblight.conf


> For a arduino MEGA,
> > $ sudo cp ~/boblight-read-only/arduino/mega.conf /etc/boblight.conf


> Next put the arduino sketch onto your arduino. For simply a arduino MEGA or Duemilanove, open the
> sketch located at ~/boblight-read-only/arduino/boblight\_arduino\_pwm/boblight\_arduino\_pwm.pde in
> the arduino IDE.

> The wiring for the arduino is as follows:

> For duemilanove,
> > connect the first LED to pins 3,5,6 (which correspond to R,G,B).
> > and the second LED to 9,10,11.
> > Wire all the LED's ground to the ground on your arduino.



> For MEGA,
> > connect the first LED to pins 2,3,4 (which correspond to R,G,B).
> > the second LED to pins 5,6,7.
> > the third LED to pins 8,9,10.
> > and the fourth LED to pins 11,12,13.
> > Wire all the LED's ground to the ground on your arduino.

Fifth step: Testing the lights:

> Plug your arduino into your computer's USB port and run the command:
> > $ boblightd

> Test your lights by running in another terminal:
> > $ boblight-constant FF0000
> > This should output the color RED. Kill this process and run:
> > $ boblight-constant 00FF00
> > This should output the color GREEN. Kill this process and run:
> > $ boblight-constant 0000FF
> > This should output the color BLUE. Kill this process.


> If a color wasn't output, or the wrong color was displayed you should go check the wiring of your
> arduino.

> Depending on how your using boblight, you should run the correct boblight client.
> To have the colors change based on the image being displayed on the screen you should
> use boblight-X11.

> boblight-X11 is known not to work in full screen with certain AMD Radeon cards with the closed source
> drivers. Some will work with the free Radeon drivers.

> If you are running boblight-X11 over ssh do:
> > $ export DISPLAY=:0.0


> To list various options for boblight-X11 you can run boblight-X11 -l and for help boblight-X11 -help

> An example one could use is:
> > boblight-X11 -x -i 0.03 -o value=5.0 -o saturation=2.0 -o speed=60.0

Written by: jjrh