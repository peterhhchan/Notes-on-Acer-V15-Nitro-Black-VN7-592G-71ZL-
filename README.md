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


On August 20, 2016 I purchased:
*  INTEL® SSD 600P Series 512GB M.2 **($270 CAD, ~$200 USD)**

Upgrade process
Used these guides for inspiration: [[1]] (http://www.myfixguide.com/manual/acer-aspire-v-nitro-vn7-591g-disassembly/), [[2]] (https://www.amazon.com/gp/customer-reviews/RGW9QPAQARUB/ref=cm_cr_pr_rvw_ttl?ie=UTF8&ASIN=B015XBKY6U), [[3]] (http://laptopmedia.com/highlights/inside-acer-aspire-v15-nitro-black-edition-vn7-591g-gtx-960m-disassembly-internal-photos-and-upgrade-options/). In addition, I found the Customer Questions and Answers section on Amazon to be very helpful [[4]] (https://www.amazon.com/Acer-Edition-VN7-592G-71ZL-15-6-inch-Notebook/dp/B015XBKY6U).

Upgrading this machine was not a trivial matter, and I would do not it again in the future.  Access to the components is under the keyboard, instead of underneath the machine.  In fact, changing the RAM module involved removing the motherboard entirely, and I found the process of disconnecting the board from the case a very nerve-wracking process.

Ensure you reconnect the ribbon between the keyboard and motherboard properly.  It came loose for me the first time, and I had to open up the machine again.  

Ensure you remember where each screw originated from.  I read online that one particular screw (the one with the battery icon beside it) is specific to that slot.  My machine would not boot up with another screw in its place.

Dual booting Windows 10 and Linux from the same drive
This process was even more difficult than upgrading the parts in the machine, and the motivation for writing this document.  
1. Install Windows 10
I created a Windows 10 bootable USB flash drive and installed Windows 10 normally on the SSD.  
A windows product key was not required. If you are wondering why, read this article.  
There are 3 USB ports on this machine, I had to use the USB3 port furthest from the screen 
2. Install Xubuntu
Disable fast startup in Windows 10.
I left UEFI enabled, but secure boot had to be disabled.  In order to modify the secure boot setting, you first need to set a password for the BIOS.
Initially, when I tried booting Xubuntu from the flash drive, the installation would continuously crash or hang.  I fixed this problem by adding “nomodeset” to the boot arguments.  (I modified the lines directly in grub on my flash drive).  
During the installation process, I manually created my own partitions instead of selecting the “install Xubuntu alongside Windows” option.
After installation, instead of rebooting immediately, I installed efibootmgr and changed the boot order such that ubuntu booted first.  (There may be more than one copy of xubuntu listed, I placed them all above Windows Boot Manager).  I used this post as a guide.
The machine upon rebooting will still boot into Windows.  The final change I had to do was install easyuefi, and then added a new Windows Boot Manager entry that pointed to grubx64.efi instead of Microsoft’s Boot\bootmgfw.efi.  
3. Final Steps
The firmware for the wireless card was not included in the distro I downloaded.  Getting the 4.3 kernel solved my problem.  However, like other users online, I have experienced occasionally problems with my wifi connection.  I would occasionally lose internet, and had to disconnect and reconnect.  

Update August, 2016.
The SSD drive failed as I was working.  
