# Notes-on-Acer-V15-Nitro-Black-VN7-592G-71ZL-

On December 19, 2015 I purchased the following:

*  	Acer Aspire V15 Nitro Black Edition VN7-592G-71ZL **($1,300 CAD, ~$1000 USD)**
  * 6th Generation Intel Core i7 6700HQ (2.60 GHz) 
  * 8 GB Memory 
  * 1 TB HDD 
  * NVIDIA GeForce GTX 960M 4 GB GDDR5 
  * 15.6" Windows 10 Home 64-Bit
  * 15.6” IPS FHD 1920x1080
  * 5.07 lbs

 
* ADATA SP900 M.2 2280 512GB Solid Sate Drive **($240 CAD, ~$180 USD)**
* HyperX Impact 16GB (2 x 8G) 260-Pin DDR4 SO-DIMM DDR4 2400  **($150 CAD, ~$115 USD)**


##Upgrading Hardware##
Used these guides for inspiration: [[1]] (http://www.myfixguide.com/manual/acer-aspire-v-nitro-vn7-591g-disassembly/), [[2]] (https://www.amazon.com/gp/customer-reviews/RGW9QPAQARUB/ref=cm_cr_pr_rvw_ttl?ie=UTF8&ASIN=B015XBKY6U), [[3]] (http://laptopmedia.com/highlights/inside-acer-aspire-v15-nitro-black-edition-vn7-591g-gtx-960m-disassembly-internal-photos-and-upgrade-options/). In addition, I found the Customer Questions and Answers section on Amazon to be very helpful [[4]] (https://www.amazon.com/Acer-Edition-VN7-592G-71ZL-15-6-inch-Notebook/dp/B015XBKY6U).

Upgrading the hardware on this machine was not a simple matter.  To access the motherboard, the keyboard had to be removed, which involved using a prying tool to lift up the keyboard, and then disconnecting the connectors between the keyboard and touchpad from the motehrboard.  Inserting the SSD drive into the M.2 slot was straightforward.

However, as the RAM modules were located underneath the motherboard, I had to detach the motherboard completely.  Removing the motherboard and then putting it back in the laptop was by far the most difficult process, with lots of bending and twisting of the motherboard.  I did not have high hopes of my laptop surviving the upgrade and definitely would not do it again. 

**N.B.**
* Ensure you reconnect the ribbon between the keyboard and motherboard properly.  It came loose for me the first time, and I had to open up the machine again.  

* Ensure you remember where each screw originated from, in particular the two screws in center.  I read online that one particular screw (the one with the battery icon beside it) is specific to that slot.  My machine would not boot up with another screw in its place.

##  Dual booting Windows 10 and Linux from the same drive ##
This process was even more difficult than upgrading the parts in the machine, and the motivation for writing this document.  

1. **Install Windows 10**

  * I created a Windows 10 bootable USB flash drive and installed Windows 10 normally on the SSD.  
  * A windows product key was not required. If you are wondering why, read this article on [digital entitlements] (http://www.pcworld.com/article/2970075/windows/why-you-cant-find-your-product-key-after-upgrading-to-windows-10.html).  
  * There are 3 USB ports on this machine, only the USB3 port furthest away from the screen worked for booting.

2. **Install Xubuntu 15.04**

  * Disable fast startup in Windows 10.
  * I left UEFI enabled, but secure boot had to be disabled.  In order to modify the secure boot setting, you first need to set a password for the BIOS.
  * Initially, when I tried booting Xubuntu from the flash drive, the installation would continuously crash or hang.  I fixed this problem by adding “nomodeset” to the boot arguments.  (I modified the lines directly in grub on my flash drive).  
  * During the installation process, I manually created my own partitions instead of selecting the “install Xubuntu alongside Windows” option.
  * After installation, instead of rebooting immediately, I installed efibootmgr and changed the boot order such that ubuntu booted first.  (There may be more than one copy of xubuntu listed, I placed them all above Windows Boot Manager).  I used this [post](http://forum.notebookreview.com/threads/linux-windows-dual-boot-setup-guide-gpt-uefi-edition.729142/) as a guide.
  * The machine upon rebooting still booted into Windows.  The final change I had to do was install [easyuefi](http://www.easyuefi.com/index-us.html), and then added a new Windows Boot Manager entry that pointed to grubx64.efi instead of Microsoft’s Boot\bootmgfw.efi.  

3. **Final Steps**

  * The firmware for the wireless card was not included in the distro I downloaded.  Getting the 4.3 kernel solved my problem.  However, like other users online, I have experienced occasionally problems with my wifi connection.  I would occasionally lose my wifi connection, and had to disconnect and reconnect.  

##Update August, 2016.##
The SSD drive failed as I was working, which I replaced with a INTEL® SSD 600P Series 512GB M.2 **($270 CAD, ~$200 USD)**
The NVMe support on the new SSD was noticeably faster.

This time, I decided to dual-boot plain old Ubuntu 16 alongside Windows 10.  The installation this time was much easier.  There were no problems with the graphics drivers, and I was able to use the Ubuntu installation option of installing alongside Windows successfully.  I did however had to create a boot entry in the UEFI for Ubuntu.  
