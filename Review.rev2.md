# The Local Deck Revisited

for my orginal review and feedback please see here - https://github.com/MichaelMKKelly/LocalDeck-Review/blob/main/Review.rev1.md

This review will be focused on the Rev2 and my experience with it during unboxing and onboarding.

NB: I have not used the device for any length of time as of yet. but will add further information if I find anything else worth noting.

## Reasons for getting

I have been fairly happy with my [orginal localdeck setup](https://github.com/MichaelMKKelly/LocalDeck-Light-Switch-Mount)

I was considering getting another for my Desk and knew that there was a hardware revision coming soon so I was looking out for it.

then i got an email

```
Our previously sold-out flagship has finally made its grand return — and it’s better than ever.

We’ve spent time refining the circuitry to deliver an even smoother, more reliable experience. Whether you're expanding your smart home or buying for the first time, now’s the perfect moment to grab your new LocalDeck.
```
So I decided to buy one for use at my desk and gives me a reason to examine the revisions made to the product

## Initial Unboxing and examination

Well packed as come to expect from LocalBytes.

based on the experience the first time the first things i checked were:
- Was the faceplate intact
- did the PSU output an expected voltage

The faceplate initially looked okay but more on this later

the included PSU showed 5.2v on usb test meter so that looks good too

### examination of physical changes and observations

The USB port on the side no longer has the retention issue that REV 1 did because it has had the hole widened and works as expected

the read of the unit now has a small hole that allows you to "paperclip" the boot button in case of major firmware issue which is a good change.

one of the T8 screws holding the board in place was definitely harder to remove than the others but this is likely a minor build process tolerance issue and did not cause a major problem

then we get to look at the back of the board itself

![2025-05-15-15-49-12-238](https://github.com/user-attachments/assets/664a51af-bbdd-49c5-96a4-dbd087060c72)

The major differences are that each LED now appears to have a capacitor attached which I imagine is to solve the flickering issue of the REV 1, and also J1 has now changed from previously being a 2 pin throughhole header it is now a 5 pin header but only 2 are throughhole which are the power and GND, same as REV 1.

![image](https://github.com/user-attachments/assets/c16ab45e-7858-42fa-889d-e2c43a32aafe)

the new additions are just pads most likely used for factory programming with pogo pins:
- D- - This is a USB Data pin
- D+ - This is a USB Data pin
- 9 - This is connected to the boot switch pin which is pulled low by the boot button

I don't really think these have any useful purpose to the end user and are designed to make factory flashing easier

There is still the issue that when using the keyhole connectors to mount the device the screws may short pins on the rear of the board.
This is not an easy problem to solve and is probably more my paranoia than a real problem but I opted to put a couple of pieces of electrical tape in place to be sure

![image](https://github.com/user-attachments/assets/9b4ab4fc-3dea-4f4b-9a3c-c8c147a18a69)

There are probably some other changes however there was nothing that I really noted.

## Actually building the unit up

I felt that snapping the front panel into place was a bit more difficult than I remember it being with a REV 1 but as this is not a side by side comparison so its hard to tell.

I did notice at this stage that one of the clips appeared to be broken off the frontplate.

![image](https://github.com/user-attachments/assets/3ec9ecd3-ad0a-4a3a-9bb8-2995e52042f4)

I am not sure if it came this way or it was my handling of it whilst trying to snap it in place then lost the piece on my desk somewhere. I am happy to give the benefit of the doubt on this one that it was my fault...
however the fact that I could have accidentally without noticing may be its own problem.

it does not really cause any issues as the others hold it in place fine and it doesn't overly bother me by itself.

the frontplate however does seem to have some other imperfections possibly from the manufacturing process. whilst the camera flash here does make it look worse than it is in normal light there are some noticeable issues.

![image](https://github.com/user-attachments/assets/c1ac8721-0b44-4014-b72b-5edc47f99074)
![image](https://github.com/user-attachments/assets/95428a1f-089f-40cc-9c33-214cb54d7379)
![image](https://github.com/user-attachments/assets/017ea5b1-a034-4c56-b379-3eafaff65e7a)

Although I don't plan to use them I did try the included brackets to see how they fit and noted that the larger of the bracket ends is too wide to hook into the casing (maybe i am doing something wrong?)

smaller

![image](https://github.com/user-attachments/assets/1510f9c6-9fd6-4988-ba38-0af513ae4e12)

bigger

![image](https://github.com/user-attachments/assets/cc24a498-f042-4aa2-9a77-9d37a2010eb8)

you can see that the bigger is slightly too big

## Onboarding of the unit into Home Assistant

This did not go well for reasons that are hard to tell...

If I was to guess I would say that something went wrong with the factory firmware flash and something was corrupted somewhere.

This is my story...

### Attempt to onboard using wifi
I connected a device to its broadcast AP which connected however i could not get any meaningful response from the UI that should be accessible at 192.168.4.1
This was marginally annoying but after a few minutes I opted to move on.

### attempt to onboard using bluetooth
I attempted this first with an Android Phone with no success. just tried for a while until timed out.

Then I tried using Windows Desktop with a bluetooth adapter. This did seem to work eventually but took a while. The device appeared on the network and could be added to HA, but it had no entities in HA and it turned out that it did not want to stay connected to my network. on reboot it connected then fell off straight away... very strange.

The ESPHome Builder did see it briefly and I was able to compile a firmware but not write as it dropped off so I took the firmware as a file and flashed it via USB using the ESPHome web tool. This still had the disconnecting problem.

### treat it like a fresh dev board and build from there.

At this point I deleted all instances of the device from HA and used the ESPHome web tool and prepared it as a brand new blank and basic ESP32 device and connected it to my wifi.

This seemed to have the device stable on my network so I added it to home assistant and adapted it into ESPHome addon.

I was then able to add the YAML to get the device working in the stock manner I expected.

I do not totally understand what went wrong and where but in the end I got there...

## Using the device

As with my first LocalDeck, I do not plan to use the Configurator Tool as recompiling and flashing the firmware for a configuration change seems silly to me...

However in fairness I am probably an "advanced user" and I am able to replicate the functionality of leds changing to follow states and whatnot easily with an automation.

I feel blueprints that help achieve this would be a better option as it stops the need for users to use the builder tool and adopt the deck into it.

Another option might be to create a "virtual integration" for Home Assistant which sits on top of and depends on the ESPHome integration but can add extra configuration.

However, that's just my opinion and I am also absolutely sure people are happy with the current "designed method of use".

At this point there is not much functional difference between Rev 1 and Rev 2.

I don't see why there will be any issues setting it up to work the way I want it

I intend to use it with a [45 dregree backbox](https://www.amazon.co.uk/dp/B09QMN3ZGJ) instead of the stock stand brackets as it is more solid and provides an angle that works better for me. The keyhole screws make this easy.

It sits under my monitor nicely

![image](https://github.com/user-attachments/assets/34b7ce3e-89e7-46ee-852e-66bc67b22c11)

It will look even better when I have the keycaps sorted out and put in place.


### Final Conclusions
Despite the problems that I have had, I do like the LocalDeck and this hardware revision does definitely tidy up some of the issues from the original release.

It would be nice to see a revision that adds an IO expander to control the switches which would then in turn free up GPIO pins which could be wired to a pinheader which would allow for customisation of the device to add extra functionality. Perhaps even a "Grove Port" to expose i2c which would allow for a variety of off the shelf accessories to be added.
