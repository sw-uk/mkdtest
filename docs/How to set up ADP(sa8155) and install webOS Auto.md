 

****

  - [Cabling](#HowtosetupADP\(sa8155\)andinstallwebOSAuto-Cabling)
      - [USB-to-Serial](#HowtosetupADP\(sa8155\)andinstallwebOSAuto-USB-to-Serial)
      - [Fastboot Connection (= EDL Connection)](#HowtosetupADP\(sa8155\)andinstallwebOSAuto-FastbootConnection\(=EDLConnection\))
          - [Fastboot download mode (if you can't enter the fastboot mode, go to section 0.)](#HowtosetupADP\(sa8155\)andinstallwebOSAuto-Fastbootdownloadmode\(ifyoucan'tenterthefastbootmode,gotosection0.\))
      - [Primary Display and Power](#HowtosetupADP\(sa8155\)andinstallwebOSAuto-PrimaryDisplayandPower)
  - [0. Prepare ADP for first time software download (in case no image on your target board)](#HowtosetupADP\(sa8155\)andinstallwebOSAuto-0.PrepareADPforfirsttimesoftwaredownload\(incasenoimageonyourtargetboard\))
      - [If your board has pre-installed Android OS or can be boot as fastboot mode, you can skip this section. go to appendix](#HowtosetupADP\(sa8155\)andinstallwebOSAuto-Ifyourboardhaspre-installedAndroidOSorcanbebootasfastbootmode,youcanskipthissection.gotoappendix)
      - [0) Switch to EDL mode](#HowtosetupADP\(sa8155\)andinstallwebOSAuto-0\)SwitchtoEDLmode)
      - [1) Install QPST.](#HowtosetupADP\(sa8155\)andinstallwebOSAuto-1\)InstallQPST.)
      - [2) Run QFIL.](#HowtosetupADP\(sa8155\)andinstallwebOSAuto-2\)RunQFIL.)
      - [3) Connect your ADP via EDL Connection(described in Cabling section) and power it on.](#HowtosetupADP\(sa8155\)andinstallwebOSAuto-3\)ConnectyourADPviaEDLConnection\(describedinCablingsection\)andpoweriton.)
      - [4) UFS provisioning – this task can be performed only once](#HowtosetupADP\(sa8155\)andinstallwebOSAuto-4\)UFSprovisioning–thistaskcanbeperformedonlyonce)
      - [5) Re-Launch QFIL](#HowtosetupADP\(sa8155\)andinstallwebOSAuto-5\)Re-LaunchQFIL)
      - [6) CDT programming](#HowtosetupADP\(sa8155\)andinstallwebOSAuto-6\)CDTprogramming)
      - [7) Reboot and verify](#HowtosetupADP\(sa8155\)andinstallwebOSAuto-7\)Rebootandverify)
  - [1. Build webOS Auto for ADP](#HowtosetupADP\(sa8155\)andinstallwebOSAuto-1.BuildwebOSAutoforADP)
      - [1) Prerequisites](#HowtosetupADP\(sa8155\)andinstallwebOSAuto-1\)Prerequisites)
      - [2) Clone build repository and build](#HowtosetupADP\(sa8155\)andinstallwebOSAuto-2\)Clonebuildrepositoryandbuild)
  - [2. Flashing](#HowtosetupADP\(sa8155\)andinstallwebOSAuto-2.Flashing)
      - [1) Fastboot access](#HowtosetupADP\(sa8155\)andinstallwebOSAuto-1\)Fastbootaccess)
      - [2) Flash via Fastboot](#HowtosetupADP\(sa8155\)andinstallwebOSAuto-2\)FlashviaFastboot)
      - [3) Enable early ethernet (It is needed at once)](#HowtosetupADP\(sa8155\)andinstallwebOSAuto-3\)Enableearlyethernet\(Itisneededatonce\))
  - [3. Appendix](#HowtosetupADP\(sa8155\)andinstallwebOSAuto-3.Appendix)



# **Cabling**

## **USB-to-Serial**

You can get the serial console access with the designated USB port. (See the picture below.)

Connect ADP and your host machine via micro-USB to USB cable, then use a console terminal application on your host.

![](/download/attachments/146037432/image2019-8-13%2012%3A3%3A50.png?version=1&modificationDate=1565665431000&api=v2)

## **Fastboot Connection (= EDL Connection)**

To connect your device via Fastboot, use a USB(M)-to-USB(M) cable as pictures below.

![](/download/thumbnails/146037432/image2019-8-13%2011%3A57%3A46.png?version=1&modificationDate=1565665067000&api=v2)  
![](/download/thumbnails/146037432/image2019-8-13%2011%3A59%3A27.png?version=1&modificationDate=1565665167000&api=v2)

You have to use USB-B port from the target.

### **Fastboot download mode (if you can't enter the fastboot mode, go to section 0.)**

To enter the download mode, press and hold 'down arrow key' from your USB-to-serial console terminal when you turn ADP on. (This must be done in non-EDL mode. turn S3-pin 7 off.)

If it succeeds, you will get messages from the console terminal as below.

    .....
    Fastboot: Initializing...
    Fastboot: Processing commands
    Failed to get the graphics output protocol.
    Failed to get the graphics output protocol.
    Failed to get width or height
    Failed to get the graphics output protocol.
    Failed to get the graphics output protocol.
    Unable to show fastboot menu on screen: Out of Resources
    Dev_Common_Speed: Bus Speed: High
    DwcGetNextEvent:Evt: UEFI AXI reordering
    Dev_Common_Speed: Bus Speed: High

Open another shell and you can see the fastboot device via below command.

    $ fastboot devices
    49c93203        fastboot

 

## **Primary Display and Power**

See the picture below for the primary display port. (TBD secondary display port)

![](/download/attachments/146037432/image2019-8-13%2012%3A3%3A17.png?version=1&modificationDate=1565665398000&api=v2)

# **0. Prepare ADP for first time software download (in case no image on your target board)**

  - **Qualcomm's pre-built image can be downloaded from <http://fileswp.lge.com/auto/adp/sa8155p-lv-0-1_hlos_dev_5.3a_complete.tar.gz> (md5sum: 20cfdf2eac9a1109c1bcd4456cc2bd4a)**

  - **You also need QPST installer. Download it from <http://fileswp.lge.com/auto/adp/tools/QPST_2.7.474.zip> (md5sum: ecfed62325fc1be6f7be96404e34c8d0)**

  - **You may need to install Qualcomm USB driver on your windows PC. (It will be likely installed automatically when you connect your ADP via Fastboot Connection.)**

  - #### If your board has pre-installed Android OS or can be boot as fastboot mode, you can skip this section. go to appendix

When the target device has no image installed, the following tasks must be performed:

#### 0\) Switch to EDL mode

  - In order to download the initial image, you need to switch your ADP to EDL mode.  
    Switch the chipset module switch S3-pin 7 on. See the picture below.  
    ![](/download/attachments/146037432/image2019-8-13%2011%3A59%3A0.png?version=1&modificationDate=1565665141000&api=v2)

#### 1\) Install QPST.

#### 2\) Run QFIL.

You can find QFIL.exe under C:\\Program Files (x86)\\Qualcomm\\QPST\\bin.

#### 3\) Connect your ADP via EDL Connection(described in Cabling section) and power it on.

#### 4\) UFS provisioning – this task can be performed only once

  - In QFIL main window, select Configuration \> FireHose Configuration. Then you will get the screen as below.

  - Choose Device Type as ufs and check Provision.  
    ![](/download/attachments/146037432/image2019-8-13%2011%3A57%3A7.png?version=1&modificationDate=1565665027000&api=v2)

  - In QFIL main window, make sure the serial port connection is detected properly. If not, try Select Port button to select a proper port.  
    ![](/download/attachments/146037432/image2019-8-13%2012%3A0%3A23.png?version=1&modificationDate=1565665224000&api=v2)

  - Select the path for the Programmer path(\<target root\>\\boot\_images\\QcomPkg\\SDMPkg\\855\\Bin\\AU\\RELEASE\\prog\_firehose\_ddr.elf)

    and Provision Xml(\<target root\>\\common\\config\\ufs\\provision\\provision\_default.xml) and click on Provision.

    ![](/download/attachments/146037432/image2019-8-13%2011%3A57%3A17.png?version=1&modificationDate=1565665038000&api=v2)  
    ![](/download/attachments/146037432/image2019-8-13%2017%3A18%3A9.png?version=1&modificationDate=1565684301000&api=v2)

#### 5\) Re-Launch QFIL

  - Now you will see the download screen as below. Make sure you get the correct serial port.  
    ![](/download/attachments/146037432/image2019-8-13%2012%3A0%3A23.png?version=1&modificationDate=1565665224000&api=v2)

<!-- end list -->

  - Select a build type. It is recommended to use the Meta Build type.  
    ![](/download/attachments/146037432/image2019-8-13%2012%3A0%3A3.png?version=1&modificationDate=1565665204000&api=v2)

<!-- end list -->

  - Click Load Content and locate the contents.xml file at a top-level directory for the project tree.  
        - Automatically selected the path for the Programmer path(\<target root\>\\boot\_images\\QcomPkg\\SDMPkg\\855\\Bin\\AU\\RELEASE\\prog\_firehose\_ddr.elf) when you load content XML.  
       (if not, you should select Programmer path via 'Browse')  
    ![](/download/attachments/146037432/image2019-8-13%2012%3A1%3A1.png?version=1&modificationDate=1565665262000&api=v2)

<!-- end list -->

  - Click 'Download Content'.
  - You should see the successful message once done. **Then turn the S3-pin 7 off to exit from EDL mode.**

#### 6\) CDT programming

  - Set your ADP to Fastboot download mode(described in Cabling section). And download adp\_0.1.0.bin file via fastboot command.

        $ fastboot devices
        49c93203        fastboot
        $ fastboot flash cdt <<target root>>/adp_0_1.0.bin

#### 7\) Reboot and verify

  - If the image is flashed properly and everything mentioned above is done, then you should see weston running from the display.
  - You can log-in from the console with this credential - root/oelinux123
  - **If there are some problems while booting up(eg. kernel crash), try extra flashing described in Appendix.**  


 

# **1. Build webOS Auto for ADP**

#### 1\) Prerequisites

  - Prepare the linux host machine (Higher than Ubuntu-17.04)

  - Run the prerequisites script (build-webos-auto/scripts/prerequisites.sh)

  - Your ADP is properly working by installing Qualcomm's image.

#### 2\) Clone build repository and build

 

  - Clone build-webos-auto

<!-- end list -->

    $ git clone ssh://gpro.lge.com/webos-auto/build-webos-auto
    $ cd build-webos-auto
    $ ./mcf sa8155
    $ source oe-init-build-env

 

  - Add mirror server configuration and Build

<!-- end list -->

    $ vi ~/.gitconfig
    Add below lines

    [url "ssh://mirrorswp.lge.com/github.com/enyojs/"]
            insteadOf = git://github.com/enyojs/
    $ bitbake webos-auto-image

 

 

 

 

# **2. Flashing**

#### **1) Fastboot access**

  -   - Set your ADP to Fastboot download mode. Your ADP should be seen via fastboot command.

            $ fastboot devices
            49c93203        fastboot

#### **2) Flash via Fastboot**

  -   - **Build artifacts are in \<build top dir\>/BUILD/deploy/images/sa8155/.**

      - **Kernel (needed whenever you change the kernel or kernel modules)**

            $ fastboot flash boot_a sa8155-boot.img

  -   - **RootFS**

            $ fastboot flash boot_a sa8155-boot.img
            $ fastboot flash system_a webos-auto-image-sa8155.rootfs.ext4
            $ fastboot reboot (ignore uart debug message. wait several seconds)

        **  
        **

      - ****Initialize UserData using the default image (needed whenever you flash a different RootFS image)****

        First, download [sa8155-usrfs.ext4](/download/attachments/146037432/sa8155-usrfs.ext4?version=2&modificationDate=1568716282000&api=v2) to your host machine. Then flash it to userdata partition.

            $ fastboot flash userdata sa8155-usrfs.ext4
            target reported max download size of 805306368 bytes
            erasing 'userdata'...
            OKAY [  0.078s]
            sending 'userdata' (33710 KB)...
            OKAY [  1.310s]
            writing 'userdata'...
            OKAY [  0.002s]
            finished. total time: 1.390s

      - **Reboot (It takes a few minutes for the first time.)**

            $ fastboot reboot

#### **3) Enable early ethernet (It is needed at once)**

  -   - **Run commands as below on the target. Use your own addresses to avoid collisions.**

            $ cd /tmp
            $ echo "192.168.225.14#FE80:CD00:0000:0CDE:1257:0000:211E:729C#3c:52:82:5d:0f:f6#" > emac.bin
            $ dd if=emac.bin of=/dev/disk/by-partlabel/emac
            $ reboot

# **3. Appendix**

  -   - You can flash Qualcomm's image per partition by running fastboot\_complete.py given in the pre-built image tarball.

        Enter Fastboot download mode and run commands as below from your host machine.

            $ cd <target root>/common/build
            $ python fastboot_complete.py --st=ufs
            $ fastboot flash cdt <<target root>>/adp_0_1.0.bin
            $ fastboot reboot

        Go to webOS Flashing.
