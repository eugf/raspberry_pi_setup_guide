# <ins>Raspberry Pi Setup Guide</ins>
### Written for [Genspace's Open Plant Community Project](https://www.genspace.org/community-projects)

  The goal of this guide is to create a minimal equipment, lowest-cost setup possible for a Raspberry Pi (including associated peripherals) in the shortest setup time, intended for new users to get up and running quickly. This is going to be a "headless setup" meaning no peripherals, such as, a screen, keyboard, or mouse are going to be used directly on the Raspberry Pi 0 W. The Raspberry Pi 0 line needs adapters to fit their micro sized ports, which can be a limiting factor for a quick setup. Instead, we'll be controlling everything wirelessly from another computer. Additionally, I've elected to use the full-fledged Raspberry Pi OS instead of the minimal one mainly because it includes Python 3, but also because the desktop interface may be easier for beginners should they choose to use that in the future.

![Rpi0W hardware-labelled+cropped](https://user-images.githubusercontent.com/12764347/90338534-40102d80-dfb8-11ea-94ee-dae62fd3cc1c.jpg)

### <ins>PREREQUISITES</ins>

### What you'll need (physically):
- Raspberry Pi 0 W
- microSD card (>= 8GB)
- microSD card adapter
- 5V (2.5A) power supply
- Windows/Mac computer with SD card reader

### What you'll need (digitally):
- Raspberry Pi OS (previously called Raspbian OS), pick one:
  - [ZIP](https://downloads.raspberrypi.org/raspios_full_armhf_latest)
  - [TORRENT](https://downloads.raspberrypi.org/raspios_full_armhf_latest.torrent)
    - NOTE: if you can torrent, that's much faster, the ZIP file seems to be speed limited no matter how fast your internet connection is
- [Balena Etcher](https://www.balena.io/etcher/)
- Windows users: [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)
  - Under Package Files > MSI: 
      - Choose the 64-bit installer if your OS can support it, if you're not sure what you have, it's fine to use 32-bit
- Mac users: SSH is built into the command line already 

### Let's get started:

##### <ins>STEP 1 - Start by downloading all the above links (this could take awhile) and assemble your physical pieces</ins>

- Slot your microSD card into the microSD card adapter
  - This goes into the the SD card slot on your computer (if you don't have one you'll need to get an adapter or dongle)

![Rpi0W-setup](https://user-images.githubusercontent.com/12764347/90348240-247e4480-e003-11ea-87dd-33b412b37371.jpg)

##### <ins>STEP 2 - Flash the OS onto the microSD card</ins>

- Open up Balena Etcher

  ![Rpi0W-Etcher-flash1](https://user-images.githubusercontent.com/12764347/90342412-34cbfa80-dfd6-11ea-8290-05c918884d1b.png)

  - Flash from file
    
  ![Rpi0W-Etcher-flash2](https://user-images.githubusercontent.com/12764347/90350323-c9505000-e00a-11ea-926f-03f6926c7f62.png)

  - Select your Raspbian OS ZIP file 

  ![Rpi0W-Etcher-flash3](https://user-images.githubusercontent.com/12764347/90342502-ccc9e400-dfd6-11ea-93c4-7620bf797437.png)

  - Select target

  ![Rpi0W-Etcher-flash4](https://user-images.githubusercontent.com/12764347/90342511-d6ebe280-dfd6-11ea-940b-17b5919b863f.png)

  - Check your microSD card
    - Size should be anywhere from 8 - 64 GB
      - Sizes >= 64 GB will need to be reformatted, see [here](https://www.raspberrypi.org/documentation/installation/sdxc_formatting.md)
    - Location should NOT be the main C:\ drive (this is hidden so you don't wipe your entire computer)

  ![Rpi0W-Etcher-flash5](https://user-images.githubusercontent.com/12764347/90342522-ee2ad000-dfd6-11ea-876f-16ddd4eccb05.png)

  - Flash!
    - Windows users: you may need to grant permission to the command line to start the flashing process by selecting "Yes"
 
  ![Rpi0W-Etcher-flash6](https://user-images.githubusercontent.com/12764347/90350328-cce3d700-e00a-11ea-925e-4e1cb7e2cde9.png)


##### <ins>STEP 3 - Prepare the boot partition</ins>

If you scroll to the top of this page, you will see the [boot_files](https://github.com/eugf/raspberry_pi_setup_guide/tree/master/boot_files) folder. You can either download this entire GitHub repository and extract those two boot files, or copy and paste the contents into your own text files on your computer.
(NOTE: This part is written for a Windows computer, but the process should be fairly similarly on a Mac)

If you're copy pasting onto your own computer:
- Open up My Computer > select the microSD card (for me it's the F:\ drive) > right click somewhere away from the file names > New > Text document 
  - Right click the file > Rename > Change the name and the extension to 
    ```
    ssh
    ```
    with NO EXTENSION (be sure to delete the .txt at the end)
- Repeat these steps to make a second file, but this time copy and paste the text inside the wpa_supplicant.conf file into your blank text document
  - Change the network SSID (your wifi name) and the network PSK (your wifi password) to match your own home network
  - Save and close the file
  - Right click the file > Rename > Change the name and extension to 
    ```
    wpa_supplicant.conf 
    ```
    (be sure to delete the .txt at the end)
  
![Rpi0W-boot](https://user-images.githubusercontent.com/12764347/90416406-68fbf580-e080-11ea-82bf-b96cfc22b95f.png)

If you're using a hidden network, an unsecured network, an extremely long  password or want some special configurations, see [here](https://www.raspberrypi.org/documentation/configuration/wireless/wireless-cli.md) for more details on how to set that up

- Eject
  - Windows users: Right click the USB/attached drive icon in the bottom right of the task bar
    - Select your microSD card
      - It should say "[your microSD card drive letter] can be safely removed now"
  - Mac users: Drag the icon for the microSD card drive to the eject icon
  - If it's a spring-loaded type, you can press the card deeper into the slot and it should pop back out. If you have the kind where the SD card sticks out then it won't have a spring and can be easily removed with your fingers

![Rpi0W-Etcher-flash7](https://user-images.githubusercontent.com/12764347/90342538-026ecd00-dfd7-11ea-909c-33b757df5854.png)

##### <ins>STEP 4 - Raspberry Pi</ins>

You're finally ready to setup the physical Raspberry Pi!
- Take the microSD card out of the microSD card adapter, and slot it into the Raspberry Pi
- Connect the power plug to the slot that is labelled "PWR IN"
- You should see a green light in the corner (close to the "PWR IN" plug) if the power is on and the OS boots correctly

![Rpi0W-ON](https://user-images.githubusercontent.com/12764347/90437033-a6bc4680-e09f-11ea-8bf9-4b9a33be57e1.jpg)

##### </ins>STEP 5 - SSH</ins>

Windows users:
- Go to the Start menu > type in "cmd" > run the Command Prompt program
- Type in:
  ```
  ping raspberrypi.local 
  ```
- Make note of the IP address this returns, which in my case starts with 192.xxx.xx.xxx
  
![Rpi0W-ping](https://user-images.githubusercontent.com/12764347/90437341-319d4100-e0a0-11ea-8c13-215eb90b7928.png)

- Open up the PuTTY program > type in the IP address (or try all of them if you have multiple) > open
  - It will give you a warning, select "Yes"

![Rpi0W-SSH](https://user-images.githubusercontent.com/12764347/90437262-13374580-e0a0-11ea-90e2-eb2173240081.png)

Mac users:
- Go to your applications and open up a Terminal > type in:
  ```
  ssh pi@192.xxx.xx.xxx
  ```
  - Replace the digits after the @ symbol with your Raspberry Pi's IP address

See [here](https://www.servermania.com/kb/articles/ssh-mac/) for more info

##### <ins>STEP 6 - Logging into the Pi</ins>
Once you've successfully connected over SSH, you are now operating over the command line in the Raspberry Pi, also called "command line interface" (CLI). At this point, your computer is remotely accessing your Raspberry Pi and can run any programs from here (provided you know what to type in). But first, it will ask for the default login credentials of the Raspberry Pi, which we are going to change IMMEDIATELY for security reasons.

- Login as > pi
  - Password is > raspberry
- Type in:
  ```
  passwd
  ```
  - Enter the default password
  ```
  raspberry
  ```
  - Now enter your desired password twice
  
  ![Rpi0W-passwd](https://user-images.githubusercontent.com/12764347/90437186-edaa3c00-e09f-11ea-83a7-c396cde0ef93.png)
  
Congrats! You are now ready to start using your Raspberry Pi! 

##### <ins>STEP 7 - Handy extras</ins>

For a simple GUI based way to edit important system settings, such as:
- passwords
- wifi networks
- SSH, VNC
- overclocking
- GPIO pins, SPI, EC2 connections

You can use the command:
``` 
sudo raspi-config 
```

![sudo raspi-config](https://user-images.githubusercontent.com/12764347/90437136-d9663f00-e09f-11ea-894a-294c3d5dc3e4.png)


***One more thing: always shut down properly by typing in***
```
sudo halt
```
***The green light in the corner will blink a few times before turning off. Now you can unplug the power. Unplugging it before a proper shutdown (either from command line or from the desktop interface's shutdown button) can result in memory corruption on the microSD card which can eventually destroy the card and whatever data you had on it***
