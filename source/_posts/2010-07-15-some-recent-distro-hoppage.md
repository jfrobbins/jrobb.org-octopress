---
layout: post
title: some-recent-distro-hoppage
date: 2010-07-15-07:24:35
comments: false
categories: [jbs, distro, crunchbang, distro, distrohop, fedora, linux <br>]
---

I did have <a href="http://www.jolicloud.com/" target="_blank">Jolicloud</a> on my eeePC (900A), and it was fine for a while.  Actually, it was a pretty neat distro.  However when you try to install things using apt-get like a normal distro instead of through the "app cloud", some things stop working and it goes downhil.  This, combined with me itching to hop a couple of distros let me to switch.

 So I started out using <a href="http://www.google.com/url?sa=t&amp;source=web&amp;cd=1&amp;ved=0CBsQFjAA&amp;url=http%3A%2F%2Funetbootin.sourceforge.net%2F&amp;ei=mvY-TMfcPMGB8gbw3bWuCg&amp;usg=AFQjCNFG2iJy14ueI6PKA0HBkn1cP-KoBg" target="_blank">UNetBootin</a> to create a Live USB stick for <a href="http://distrowatch.com/fedora" target="_blank">Fedora 13</a> (LXDE), and installed on the EEE.  The eee is actually pretty well supported with Fedora, including the wireless (on the 900 model that I have, the 1100+ may be a different story).  This was okay, except that it was not optimized for the small screen, and some of the GUI prompts actually hung off of the screen.  Not to mention I was missing some "tap and click" functionality of the trackpad thing.  Total time installed.... about 4 hours.

 From this point on...I had a bit of trouble.

 <!--more-->
I now realize that my problems had a LOT to do with the drives I was using, and drive order on boot, etc.  The main drive of my EEE is a 4GB SSD.  I also have a 2GB SD card in the reader, which I intended to use as /home.  and then, the USB media was another drive (when one was used).

 I have a cd-r with <a href="http://distrowatch.com/crunchbang" target="_blank">CrunchBang</a> 10 Alpha 2 "Statler" (which I run on my other laptop), so since this release does not play nicely with live USB media, I hooked up my slim CD/DVD RW USB drive and booted the cd-r I had previously burned. Somehow, this got completely messed up and would not boot after install.  after trying to fix it for a bit, I gave up, and then I moved onto...

 <a href="http://distrowatch.com/slitaz" target="_blank">SLiTaz</a>.  This is a very small distro, about 30mb, which I ran from a USB stick.  On boot, it installs entirely into the RAM and is extremely quick.  This is much like Puppy Linux, however there is a root and standard user (<a href="http://distrowatch.com/puppy" target="_blank">Puppy</a> only has root...or that was the case the last time I used it, anyway).  I installed this to the disk, using the same setup with /(root) /home and swap partitions between the SSD and SD card. This setup would almost boot, but no kernel found-- so I just edited the GRUB prompt and got it to boot no problem.  Then, however, I could not log in as my standard user!  I could log in as root, and change passwords and anything else-- I even removed and re-added my standard user, and still could not log in.

 At this point, I was even more frustrated.  I decided to try CrunchBang Statler ONE more time.  Hooked up the USB CD drive again and reinstalled.  However THIS time I just installed all to the SSD.  worked like a charm.  After the install was setup, I got the UUID for the SD card and modified my /etc/fstab to mount it as /home.  Voila!  Everything working like a champ.

 Also, in #! 10, the trackpad works terrifically!  Tap and click, along with 2 finger scroll--which is awesome!  I like it a lot.

 Now, this brings me back to Fedora.  I was still wanting to try this out, since I had only looked at Fedora 11 very briefly, and I had actually used Red Hat (pre-Fedora) for a while from 2000 to ~2002ish.   I have an Acer Aspire Revo (which I'd written specifically about before but that was wiped out from the other host crashing), I decided to install Fedora13 on here to dual-boot with Windows7.

 I first shrunk the Windows partition using <a href="http://distrowatch.com/table.php?distribution=gparted" target="_blank">Gparted</a> which I installed onto the LiveUSB environment.  The install went very well, everything set up properly. I installed grub to the first sector of the /boot of Fedora, rather than to the MBR however, because of some issues I had read of involving Windows 7.  As I went to boot, it went straight to Windows without a hitch.  A problem, as I wanted to boot to Linux.  I then installed <a href="http://download.cnet.com/EasyBCD/3000-2094_4-10556865.html" target="_blank">EasyBCD</a> onto WIndows and added Fedora to the boot menu.  After this, it has continued to work beautifully.

 I added <a href="http://rpmfusion.org/" target="_blank">RPMFusion</a> repositories for any "Free" or "nonFree" content that is not included by default in the Fedora release.  I also used the <a href="http://www.fedorafaq.org" target="_blank">Unofficial Fedora FAQ</a> to get flash working and some other things.

 I downloaded the latest <a href="http://www.jezra.net/projects/heybuddy" target="_blank">HeyBuddy</a> RPM from <a href="http://rpm.psquid.net/" target="_blank">PSquid's site</a>.  Now I am all up to date, and doing some further exploration into Fedora.  I am liking it, so far--and I really like the LXDE interface!  I don't know if I would switch from Arch...But if I was switching, this would be a contender (As would CrunchBang).

 Alright, That's all I've got!

 

Posted by: jamba

Category: ##distro 

Tags:  #crunchbang #distro #distrohop #fedora #linux 


Published Date: Thu, 15 Jul 2010 12:24:35 +0000 

<a href="http://factorq.net/2010/07/15/some-recent-distro-hoppage/">Original URL</a> | <a href="http://factorq.net/?p=354">Original guid</a> | PostID= 354

 original filename: 126