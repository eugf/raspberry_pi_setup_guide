# Raspberry Pi Setup Guide
### Written for Genspace's Open Plant Community Project

  The goal of this guide is to create a minimal equipment, low-cost setup for a Raspberry Pi (including associated peripherals) in the shortest setup time, intended for new users to get up and running quickly. This is going to be a "headless setup" meaning no peripherals, such as, screen, keyboard, or mice are going to be used on the Raspberry Pi 0 W. The Raspberry Pi 0 line needs adapters to fit their micro sized ports, which can be a limiting factor for a setup. So instead we'll be operating everything wirelessly from another computer. Additionally, I've elected to use the full-fledged Raspberry Pi OS instead of the minimal one mainly because it includes Python 3, but also because the desktop interface may be easier for beginners should we use that in the future.

![Rpi0W hardware-labelled+cropped](https://user-images.githubusercontent.com/12764347/90338534-40102d80-dfb8-11ea-94ee-dae62fd3cc1c.jpg)

### What you'll need (physically):
- Raspberry Pi 0 W
- microSD card (>= 8GB)
- microSD card adapter
- 5V (2.5A) power supply
- computer with SD card reader

### What you'll need (digitally), please download:
- Raspberry Pi OS (previously called Raspbian OS), pick one:
  - [ZIP](https://downloads.raspberrypi.org/raspios_full_armhf_latest)
  - [TORRENT](https://downloads.raspberrypi.org/raspios_full_armhf_latest.torrent)
    - NOTE: if you can torrent, that's much faster, the ZIP file seems to be speed limited no matter how fast your internet connection is
- [Balena Etcher](https://www.balena.io/etcher/)
- Windows users: [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
  - Under Package Files > MSI: 
      - Choose the 64-bit installer if your OS can support it, if you're not sure what you have, it's fine to use 32-bit

### Let's get started:

##### 1. Start downloading all the above links (this could take awhile) and assemble your physical pieces

- Slot your microSD card into the microSD card adapter
  - This goes into the the SD card slot on your computer (if you don't have one you'll need to get an adapter or dongle, there may be a way to flash it on a phone that has a microSD card slot as well)

![Rpi0W-setup](https://user-images.githubusercontent.com/12764347/90348240-247e4480-e003-11ea-87dd-33b412b37371.jpg)

##### 2. Flash the OS onto microSD card

- Open up Balena Etcher

![Rpi0W-Etcher-flash1](https://user-images.githubusercontent.com/12764347/90342412-34cbfa80-dfd6-11ea-8290-05c918884d1b.png)

  - Flash from file
    
![Rpi0W-Etcher-flash2](https://user-images.githubusercontent.com/12764347/90350323-c9505000-e00a-11ea-926f-03f6926c7f62.png)

    - Select your Raspbian OS ZIP file 

![Rpi0W-Etcher-flash3](https://user-images.githubusercontent.com/12764347/90342502-ccc9e400-dfd6-11ea-93c4-7620bf797437.png)

  - Select target

![Rpi0W-Etcher-flash4](https://user-images.githubusercontent.com/12764347/90342511-d6ebe280-dfd6-11ea-940b-17b5919b863f.png)

    - Check your microSD card
      - Size should be between 4 - 64 GB
        - Sizes >= 64 GB will need to be reformatted, see [here] (https://www.raspberrypi.org/documentation/installation/sdxc_formatting.md)
      - Location should NOT be the C:\ drive

![Rpi0W-Etcher-flash5](https://user-images.githubusercontent.com/12764347/90342522-ee2ad000-dfd6-11ea-876f-16ddd4eccb05.png)

  - Flash!
    - Windows users: you may need to grant permission to the command line to start the flashing process by selecting "Yes"
 
![Rpi0W-Etcher-flash6](https://user-images.githubusercontent.com/12764347/90350328-cce3d700-e00a-11ea-925e-4e1cb7e2cde9.png)

  - Eject
    - Windows user: Right click the USB/attached drive icon in the bottom right of the task bar
      - Select your microSD card
        - It should then say "[microSD card] can be safely removed now"
          - Press the card into the slot, it's spring-loaded so it should pop back out

![Rpi0W-Etcher-flash7](https://user-images.githubusercontent.com/12764347/90342538-026ecd00-dfd7-11ea-909c-33b757df5854.png)


##### 3. Prepare the boot partition

##### 4. SSH 



