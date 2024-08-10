# A Review of the LocalDeck - IMCOMPLETE

A review of the new localdeck from localbytes

This can also serve as feedback for localbytes for possible future verions/products

## Who is LocalBtes and why did I buy?

Theey are a small UK company with a small range of products that I ran into whilst looking at various smart plugs and they seemed great value for money so decided to give them a go and when The products turned out to be of a reasnable quality I decided to jump in to their new localdeck product as I have some half ideas on things i might want to do with it.

I am a firm believer in judgeing a company by what it does when things go wrong and so far this has been a good 

## Getting the Product

As with any new product there are teething issues and this was no different. there was a month delay in shipping as there was an issue with the production run of the PCB's however this has been publically addressed and will be resolved.

When I first received the product the faceplatee was cracked. I beleive this happened in transit. However upon emailing a photo to localbytes they immediately shipped a replacement which arrived promptly and had no issues.

A 2nd issue was that one of the keys did not work out the box. this turned out to be a bent pin on the switch once bent back into place it worked without further issue but may have been weakened by this happening. Again - I dont think localbytes is directly to blame for this issue however perhaps they can update assembly QA prodeedure to prevent it happening to others in future.

## The LocalDeck itself

The device is a nice neat design and has 2 official options to power it both being usb-c ports. one in the lower right side of the casing and one on the rear

It appears that the designed purpose is that if its sitting on a desk the side usb-c port should be used and if its wall mounted then the rear port can be used.

Once powered up it has a wifi AP and BLE options courtesy of ESPHomee to configure it to allow you to configure it with your wireless settings.

once connected to the network home assistant picks it up as a device and also the esphome addon allows for adoption without any issue.

## The Home Assistant addon

TODO

## Hidden Features

If the PCB is removed from the housing by taking out the 4 screws and the back side is made visable we get to see the ESP32 itself and a couple of hidden extra's on the board.

SW1 - this is labled "Boot" and is a standard ESP32 debug board switch
J1 - unpopulated 2 pin header for 5v and GND

Above I mentioned that there are 2 officially supported ways to power the device however with J1 it would be very easy to add your own 5v power supply to the device and soldering directly to the throughhole connections.

## Should I buy this device?

I would say this product is designed for an intermediate and higher level home assistant user. It does seem to be in a bit of a strange place of tyring to cater to both those that want it to "just work" and those that want to tinker with it. and ends up somewhere in the middle.

If you have a working knowledge of home assistant and ESPHome devices then you will have no issues using this device. if you have a very basic home automation setup then this is not as plug and play as some other smart switches might be.

## Problems

When pressing a switch some LEDS flicker. This appears to be a known problem and is being looked at for future versions of the PCB

The side USB port when plugged in through the case doesnt allow for full insertion of a usb-c cable as the casing of the plug hits the case before it bottoms out. it plugs in and works but as a result of it not going all the back to the back of the connector it is a little loose and if getting moved on a desk is likely to become disconnected. I have tried a few USB-C cables and they all have the same issue so its not a connector tolorence issue however it could be a case toloraence issue with my specific case.

The rear USB port when sitting on a surface is very close to the surface. This makes me nervous for potential shorts if put on something or if there is a liquid spill.

when using the mounting holes to mount it to a backbox the screws that it slots onto are very close to the pins for LED08 and LED11. I am nervous that screws being a little long could result in shorts. a bit of kaptop tape on the board in these areas is probably the easy solution

Also when using the backbox mounting configuration the keyhole slots are great for simplicity but from a safety front they are a bit of an issue. someone can very easily slide it up and possibly access cables in the rear which may include live mains cables. I can see a child for example pushing it up and grabbing poking hands where they dont belong. perhaps some kind of retaining mechinism or switch to a backplate (more below)

## Suggestions for future revisions

allow for full insetion of side USB port. (mentioned above but i feel its important to highlight again)

look at making the case reversible so that the PCB can be mounted the other way around and have the USB connection on the other side. this would make it more practical for putting on either side of a desk setup.

if a GPIO pin can be freed up then exposing that to allow for pysical addons would be great.
A relay addon would be fantastic as when mounting on a standard backbox it can replace a light switch and also become a smart switch for the light switch that replaced it

the case tries to do everything. realistically perhaps changing the case to instead of directly keyholing onto the screws from a backbox it has other mounting connections and a seperate optional backplate product that you can mount on the wall over a backbox (or anywhere else) and then the main case hooks into it. this means if it gets pushed off then at most 5v DC would be exposed. this backplate could have a relay variant if addons could be added as suggested above


## My thoughts for using in a project

using the backbox mount to replace a lightswitch.
potetnitally with a 45 degree adapter to make button pressing easier.
include a 5v power supply in the backbox to power the unit.
add a relay module to replace the switching that the light switch did before being replaced.
if adding the relay module control directly to the onboard esp32 then hardcode one of the keys to switch it so that it works even
