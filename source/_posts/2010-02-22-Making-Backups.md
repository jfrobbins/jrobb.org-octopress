---
layout: post
title: Making-Backups
date: 2010-02-22-07:51:48
comments: false
categories: [jbs, qa, first, incremental, linux, arch, backup, data, linux, raid, rdup, rsync <br>]
---

Backups can be very important, no one wants to lose any of their data--<em>especially</em> if it has happened to you before.

 I have previously <a href="http://factorq.net/2009/09/30/my-adventure-installing-linux-on-softraid1-part-4/" target="_blank">setup my x64 desktop PC with softRAID</a>, so everything I have in my /home folder is mirrored across 2 drives.  However, I am not sure if I am overly paranoid, or maybe I just like to be extra secure because now I have implemented an additional backup measure.

 It started when I read <a href="http://fqnet.proboards.com/index.cgi?board=nix&amp;action=display&amp;thread=50" target="_blank">some of this stuff</a> about backups and solutions, so I decided I should probably do something similar.  The one from distrowatch really pushed me a long though, as the <a href="http://distrowatch.com/weekly.php?issue=20100208#qa" target="_blank">Q&amp;A thing</a> really made sense.

 To start off, I began by reading the ArchWiki backup tools page: <a href="http://wiki.archlinux.org/index.php/Backup_Programs" target="_blank">wiki.archlinux.org/index.php/Backup_Programs</a>.  I chose to try a few of them, I didn't like arch-backup, backerupper didn't really work the way I liked.  A few more just didn't work for me.<!--more-->
I used <a href="http://www.miek.nl/projects/rdup/index.html" target="_blank">rdup</a> (continuation of hdup, or at least made by the same developer), which worked well, but not really for the large amount of data that I am backing up.  It is a VERY flexible tool (that actualy doesn't back anything up at all!), so I tried a few different methods from creating a large .tar.gz file (26GB!), to incrementaly hardlinked backups, but I didn't care too much for it.

 <pre>#first method, creating a tarball

 rdup ~/.rdup-backup-list $SOURCEDIR | rdup-tr -Otar | gzip -c -f &gt; $DESTDIR

 #incremental style backup

 rdup-simple -zvmn ~/ $DESTDIR</pre>
In the end, I decided to go back to the tried and true, age-old: <a href="http://samba.anu.edu.au/rsync/" target="_blank">rsync</a>.  I recently put something together at work to mirror a drive I use for my software application at another locaton, and I used rsync (by using <a href="http://www.cygwin.com/" target="_blank">cygwin</a> to emulate a unix shell to run it on windows...but that's another story).  So I use rsync to run incremental backups, and I run this nightly (with a cron entry). With these flags, if nothing is updated or changed, nothing changes.  Otherwise it copies only the changes.  It works great for me!

 <pre>rsync -avzutmo --delete ~/ $DESTDIR

 </pre>
As a side note, my backup media is a USB external hard drive.

 

Posted by: jamba

Category: ##linux 

Tags:  #arch #backup #data #linux #raid #rdup #rsync 


Published Date: Mon, 22 Feb 2010 12:51:48 +0000 

<a href="http://factorq.net/2010/02/22/making-backups/">Original URL</a> | <a href="http://factorq.net/?p=240">Original guid</a> | PostID= 240

 original filename: 102