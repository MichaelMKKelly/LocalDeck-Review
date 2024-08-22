# A Review of the LocalDeck - Some Issues but a nice product from a good company

A review of the new localdeck from localbytes

This can also serve as feedback for localbytes for possible future versions/products

![image](https://github.com/user-attachments/assets/97cbbc90-2978-4f27-ac89-4e177e82145b)
Product Page - https://www.mylocalbytes.com/products/localdeck

Disclaimer:

This review is one man's opinion but I can only offer my side

Parts of this review may come across negative however in general I do like the device and think that LocalBytes is a good company that can be trusted.

## Who is LocalBytes and why did I buy?

They are a small UK company with a small range of products that I ran into whilst looking at various smart plugs and they seemed great value for money so decided to give them a go and when The products turned out to be of a reasonable quality I decided to jump in to their new localdeck product as I have some half ideas on things i might want to do with it.

I am a firm believer in judging a company by what it does when things go wrong and so far this has been an extremely good showing from LocalBytes as shown below

## Getting the Product

As with any new product there are teething issues and this was no different. There was a month delay in shipping as there was an issue with the production run of the PCB's however this has been publicly addressed and will be resolved for future runs.

When I first received the product the faceplate was cracked. I believe this happened in transit. However upon emailing a photo to localbytes they immediately shipped a replacement which arrived promptly and had no issues. from some comments on the forums it seems I was not the only one that had this issue and they are looking to resolve this in the future.

A second issue was that one of the keys did not work out the box. this turned out to be a bent pin on the switch once bent back into place it worked without further issue but may have been weakened by this happening. Again - I don't think localbytes is directly to blame for this issue however perhaps they can update assembly QA prodeedure to prevent it happening to others in the future.

A third issue cropped up during testing, there was some instability and as part of testing I discovered that the power supply included in the bundle was only putting out 4.4v which is definitely below tolerance. Upon emailing LocalBytes they again immediately shipped a replacement which promptly arrived and was up to tolerance. The supply itself appears to be a rebadged cheap chinese supply so I am sure they get a few duff ones and it's not their fault.

## The LocalDeck itself

The device is a nice neat design and has 2 official options to power it both being usb-c ports. one in the lower right side of the casing and one on the rear

It appears that the designed purpose is that if it's sitting on a desk the side usb-c port should be used and if its wall mounted then the rear port can be used.

Once powered up it has a wifi AP and BLE options courtesy of ESPHomee to configure it to allow you to configure it with your wireless settings.

once connected to the network home assistant picks it up as a device and also the esphome addon allows for adoption without any issue.

## Home Assistant

Localbytes recommends using their configurator addon which I have (so far) not used. However I have looked at how it works and it seems painful to have to recompile and reupload firmware to the board to change what a switch does.

I will probably try it out at some point but I have resisted so far. I am not a fan of this approach but that is not to say it's bad or wrong, I just dislike it.

I am not the only one that wants to go another way. There has already been a handful of people proposing alternate firmwares and configuration options to remove the need for the addon.

it does work out the box with esphome integration though and automations triggered by button presses are easy enough to set up without making it too complicated.

Perhaps it is not fair to voice an opinion when not using it in the "intended" way? Or is the intended way to tinker?

## Further Testing and Hidden Features

![image](https://github.com/user-attachments/assets/2862c8d9-fa29-478d-8efa-82bb2005ffa1)

If the PCB is removed from the housing by taking out the 4 screws and the back side is made visible we get to see the ESP32 itself and a couple of hidden extras on the board.

SW1 - this is labelled "Boot" and is a standard ESP32 debug board switch

J1 - unpopulated 2 pin header for 5v and GND

Above I mentioned that there are 2 officially supported ways to power the device however with J1 it would be very easy to add your own 5v power supply to the device and soldering directly to the throughhole connections.

The bundled supply is rated at 3A and theoretically the max of the components driving all LEDS to the max could get within striking distance of that, however in testing with all LEDS on it is not that far above an amp 1.15-1.2 was about the max that I saw. It can definitely cause problems if you use a supply with a 1A limit so ensure you use a correctly rated supply if not using the stock one. although if you opted to limit or disable the LEDS then you could probably run it on a 1A supply or maybe lees but do so at your own risk. for most people sticking with the stock supply is likely the best option.

## Should I buy this device?

I would say this product is designed for an intermediate and higher level home assistant user. It does seem to be in a bit of a strange place of trying to cater to both those that want it to "just work" and those that want to tinker with it. It ends up somewhere in the middle.

If you have a working knowledge of home assistant and ESPHome devices then you will have no issues using this device. if you have a very basic home automation setup then this is not as plug and play as some other smart switches might be.

## Problems

When pressing a switch some LED's flicker. This appears to be a known problem and is being looked at for future versions of the PCB

The side USB port when plugged in through the case doesn’t allow for full insertion of a usb-c cable as the casing of the plug hits the case before it bottoms out. It plugs in and works but as a result of it not going all the way to the back of the connector it is a little loose and if getting moved on a desk is likely to become disconnected. I have tried a few USB-C cables and they all have the same issue so it's not a connector tolerance issue. after speaking with others on the LocalBytes forum it appears this is not limited to just me and its been confirmed as a known issue that is being looked at for future versions

The rear USB port when sitting on a surface is very close to the surface. This makes me nervous for potential shorts if put on something or if there is a liquid spill.

when using the mounting holes to mount it to a backbox the screws that it slots onto are very close to the pins for LED08 and LED11. I am nervous that screws being a little long could result in shorts. a bit of kapton tape on the board in these areas is probably the easy solution

Also when using the backbox mounting configuration the keyhole slots are great for simplicity but from a safety front they are a bit of an issue. someone can very easily slide it up and possibly access cables in the rear which may include live mains cables. I can see a child for example pushing it up and grabbing or poking their hands where they don't belong. perhaps some kind of retaining mechanism or switch to a backplate (more below)

there appears to be issues with wireless connection, when viewing logs via wireless it spams and disconnects. this issue is reduced by setting "power_save_mode: none" however for this you need to disable bluetooth which means departing from the default remote backage for the source. perhaps bluetooth should just be dropped (see bwlow)


## Suggestions for future revisions

allow for full insertion of the side USB port. (mentioned above but i feel its important to highlight again)

look at making the case reversible by putting a hole in the opposite corner so that the PCB can be mounted the other way around and have the USB connection on the other side. This would make it more practical for putting on either side of a desk setup.

if a GPIO pin can be freed up then exposing that to allow for physical addons would be great.
A relay addon would be fantastic as when mounting on a standard backbox it can replace a light switch and also become a smart switch for the light switch that replaced it

The case tries to do everything. realistically perhaps changing the case to instead of directly keyholing onto the screws from a backbox it has other mounting connections and a separate optional backplate product that you can mount on the wall over a backbox (or anywhere else) and then the main case hooks into it. this means if it gets pushed off then at most 5v DC would be exposed. this backplate could have a relay variant if addons could be added as suggested above

The 4 square holes on the back of the case used for the stand could potentially  be used to mount to a backplate?

consider dropping bluetooth, it causes issues as noted above and its not used for anything except as an optional way to perform initial setup then just sits there not helping anyone. realistically people using this product are going to be fine with wifi setup.

When the device connects to home assistant the button sensors are in "unknown" station which annoys me in a way it probably shouldn't hopefully this can be fixed somehow in the future. I tried updating the firmware to add "publish_initial_state" to the button sensors but this did not work. so i ended up adding a script to publish an off state for all buttons which is called "on_client_connected:" in the api section

````
script:
  - id: init_keypad_sensors
    mode: parallel
    then:
      - lambda: >
          id(keypad_button_01).publish_state(false);
          id(keypad_button_02).publish_state(false);
          id(keypad_button_03).publish_state(false);
          id(keypad_button_04).publish_state(false);
          id(keypad_button_05).publish_state(false);
          id(keypad_button_06).publish_state(false);
          id(keypad_button_07).publish_state(false);
          id(keypad_button_08).publish_state(false);
          id(keypad_button_09).publish_state(false);
          id(keypad_button_10).publish_state(false);
          id(keypad_button_11).publish_state(false);
          id(keypad_button_12).publish_state(false);
          id(keypad_button_13).publish_state(false);
          id(keypad_button_14).publish_state(false);
          id(keypad_button_15).publish_state(false);
          id(keypad_button_16).publish_state(false);  
          id(keypad_button_17).publish_state(false);
          id(keypad_button_18).publish_state(false);
          id(keypad_button_19).publish_state(false);
          id(keypad_button_20).publish_state(false);
          id(keypad_button_21).publish_state(false);
          id(keypad_button_22).publish_state(false);
          id(keypad_button_23).publish_state(false);
          id(keypad_button_24).publish_state(false);
````

It's not a great solution but it works for now

## My thoughts for using in a project

using the backbox mount to replace a lightswitch.
potentially with a 45 degree adapter to make button pressing easier.
include a 5v power supply in the backbox to power the unit.
add a relay module to replace the switching that the light switch did before being replaced.
if I could add the relay module control directly to the onboard esp32 then hardcode one of the keys to switch it so that it works even if connection is lost. However I dont think this is possible with the current hardware revision

## Conclusion and final thoughts

Is it a good device? I would have to say: yes

Does it have problems? Again I have to say: yes

getting the first run of hardware for a device naturally comes with some risks but if you are someone that tinkers with the hardware and can adapt to the situation then it like other things from the LocalBytes lineup is a great value device that does the basics well.

If you are not someone that wants to tinker with their device then as mentioned above, this may not be the device for you. however at the price point if you want to put a little effort in then it may be worth giving it a shot.

## Further Reading

LocalDeck Product Page: https://www.mylocalbytes.com/products/localdeck-bundle

LocalDeck Documentation: https://blog.mylocalbytes.com/kb/2024-04-01/refs-localdeck/

Localbytes Website: https://www.mylocalbytes.com/

Localbytes Blog: https://blog.mylocalbytes.com/

Localbytes Forum: https://forum.mylocalbytes.com/

A Blueprint to use without the addon from nwithan8 - https://community.home-assistant.io/t/localdeck-24-button-keypad-blueprint/758230

A Custom Firmware from araa47 that uses HA's websocket API - https://github.com/araa47/local-deck-ws/
