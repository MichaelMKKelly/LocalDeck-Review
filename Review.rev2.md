# The Local Deck Revisited

for my orginal review and feedback please see here - https://github.com/MichaelMKKelly/LocalDeck-Review/blob/main/Review.rev1.md

This review will be focused on the Rev2 and my experience with it.

## Inital Unboxing and examination

Well packed as come to expect from LocalBytes.

based on the experience the first time the first things i checked were:
- Was the faceplate intact
- did the PSU otuput an expected voltage

The faceplate initally looked okay but more on this later

the included PSU showed 5.2v on usb test meter so that looks good too

### examination of physical changes and observations

The USB port on the side no longer has the retention issue that REV 1 did because it has had the hole widened and works as expected

the read of the unit now has a small hole that allows you to "paperclip" the boot button in case of major firmware issue which is a good change.

one of the T8 screws holding the board in place was definetly harder to remove than the others but this is likely a minor build process tolorence issue and didnt cause a major problem

then we get to look at the back of the board itself

![2025-05-15-15-49-12-238](https://github.com/user-attachments/assets/664a51af-bbdd-49c5-96a4-dbd087060c72)

The major differences are that each LED now appears to have a Capacitor attached which I imagine is to solve the flickering issue of the REV 1.

also J1 has now changed from previously being a 2 pin throughhole header it is now a 5 pin header but only 2 are throughhole which are the power and GND, same as REV 1.

![image](https://github.com/user-attachments/assets/c16ab45e-7858-42fa-889d-e2c43a32aafe)

the new additions are just pads most likely used for factory programming with pogo pins:
- D- - This is a USB Data pin
- D+ - This is a USB Data pin
- 9 - This is connected to the boot switch pin which is pulled low by the boot button

I dont really thing these have any useful purpsoe to the end user and are designed to make factory flashing easier

There is still the issue that when using the keyhole connectors to mount that the screws may short pins on the rear of the board.
This is not an easy problem to solve and is probably more my paranoia than a real problem but I opted to put a couple of pieces of electrical tape in place to be sure

![image](https://github.com/user-attachments/assets/9b4ab4fc-3dea-4f4b-9a3c-c8c147a18a69)

There is probably some other changes however there was nothing that I really noted.

## actually building the unit up

I felt that snapping the front panel into place was a bit more difficult than I remember it being with a REV 1 but as this is not a side by side comparason its hard to tell.

I did notice at this stage that one of the clips appeared to be broken off the frontplate.

![image](https://github.com/user-attachments/assets/3ec9ecd3-ad0a-4a3a-9bb8-2995e52042f4)

I am not sure if it came this waay or it was my handling of it whilst trying to snap it in place then lost the piece on my desk somewhere. I am happy to give benefit of the doubt on this one that it was my fault...
however the fact that I could have accidently without noticing may be its own problem.

it does not really cause any issues as the other hold it in place fine and it doesnt overally bother me by itself.

the frontplate however does seem to have some other inperfections possibly from the manufacturing process. whilst the camera flash here does make it look worse than it is in normal light there are some noticable issues.

![image](https://github.com/user-attachments/assets/c1ac8721-0b44-4014-b72b-5edc47f99074)
![image](https://github.com/user-attachments/assets/95428a1f-089f-40cc-9c33-214cb54d7379)
![image](https://github.com/user-attachments/assets/017ea5b1-a034-4c56-b379-3eafaff65e7a)

although i dont plan to use them i did try the included brackets to see how they fit and noted that the larger of the brcket ends is too wide to hook into the casing (maybe i am doing something wrong?)

smaller

![image](https://github.com/user-attachments/assets/1510f9c6-9fd6-4988-ba38-0af513ae4e12)

bigger

![image](https://github.com/user-attachments/assets/cc24a498-f042-4aa2-9a77-9d37a2010eb8)

you can see that the bigger is slightly too big

## Onboarding of the unit into Home Assistant
