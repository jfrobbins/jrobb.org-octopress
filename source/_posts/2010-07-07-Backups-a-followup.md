---
layout: post
title: Backups-a-followup
date: 2010-07-07-21:12:25
comments: false
categories: [jbs, binbash, simple_home_backup_scriptsh, this, simple, run, linux]
---

Sometime back I made <a href="http://factorq.net/2010/02/22/making-backups/">a post</a> about how I backup my data.  A <a href="http://crunchbanglinux.org/forums/topic/8486/backup-crunchbang/">recent thread</a> on the crunchbang forums brought this back to mind, so I figured I should probably document my update here as well.

 Nn my desktop I have 2 HDDs that are in a softRAID array (only /home is on the array).  and then I have a daiyly cron script which does an rsync to backup my /home to an external eSATA HDD.

 This is very simple script and just mirrors a directory (or specific directorys) in a specified location.  Use at your own risk!

 I mirror some directories from my /home onto an external eSATA drive.

 here it is:

 <pre>
<blockquote>
<pre><code>#!/bin/bash

 #simple_home_backup_script.sh

 DESTDIR=/media/backup/home #this is the path to the drive to backup TO

 #simple, but works:

 rsync -avzutmo --delete ~/Docs ~/Photos ~/vbox ~/wallpaper $DESTDIR</code></pre>
</blockquote>
<code>and my crontab entry:</code>
<blockquote>
<pre><code>#run incremental backup daily

 0 1 * * * /home/me/scripts/simple_home_backup_script.sh</code></pre>
</blockquote>
<code>I could actually make the backup run more often, since it is pretty fast, but it's not that important.  the RAID should catch most of everything, the rsync is just a backup for the backup :-)</code>
<code>
</code></pre>


Posted by: jamba

Category: ##linux 


Published Date: Thu, 08 Jul 2010 02:12:25 +0000 

<a href="http://factorq.net/2010/07/07/backups-a-followup/">Original URL</a> | <a href="http://factorq.net/?p=336">Original guid</a> | PostID= 336

 original filename: 121