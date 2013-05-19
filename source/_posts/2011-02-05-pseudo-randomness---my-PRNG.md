---
layout: post
title: pseudo-randomness---my-PRNG
date: 2011-02-05
comments: false
categories: [jbs, random, PRNG, PHP]
---

My wife <a href="http://www.etsy.com/people/NestofManyColors">sells stuff on Etsy</a>, and occasionally does some giveaway type things.
She's been using <a href="http://random.org">random.org</a>, which is a great TRUE random generator site--however, many of their better services are not free.

I then took it upon myself to set up a pretty decent Pseudo-random generator that can do the things that she needs to do:  mainly, enter a list of names and return one who would be the "winner" of the giveaway.
I set up a page to do this at <a href="http://jrobb.org/random/">jrobb.org/random</a>, and went to town making some things.  
This is all pretty simple, but it is a lot of fun to do and I can always try to make it as random as possible. :)

I wanted to have a pretty good seed, so I reused some of the code from the <a href="http://jrobb.org/blog/?article=159">jezra captcha routine</a> stuff.  I am also using the <a href="http://en.wikipedia.org/wiki/Mersenne_twister">Mersenne Twister</a>, which generates MUCH better random numbers with mt_rand() than the normal PHP rand().
[code]

function mtrand_seed() {
//try to create a more random seed
$n = ((double)microtime()*1000000);
mt_srand($n);//initial seed
$ip_address = VISITORS_IP; //get the visitors IP address
$appended_ip = $ip_address + date("zB"); //append the numeric day of the year + 	Swatch Internet time to the ip_address
$salt = genRandomString(); //add some random salt to the appended_ip
$salted_string = $appended_ip+$salt;
$md5_string = md5($salted_string) ; //get the md5sum of the salted string
$first_int = getFirstInt($md5_string); //get the first and last integer of the md5_string
$last_int = getLastInt($md5_string);

$n = ((double)microtime()*1000000);
if($first_int>$last_int)
{
$n = $first_int -$last_int + $n ;
} else {
$n = $last_int - $first_int + $n ;
}
return $n;

mt_srand($n);
}

[/code]


This seems to work rather well, but I might wind up changing it around a bit as far as how the first_int/last_int are used to manipulate the seed.

Then I read <a href="http://www.boallen.com/random-numbers.html">this post</a> which talks about random usage and image generation, and patterns that can appear from using a pseudorandom generator (mostly with the rand() function).
<a href="http://cod.ifies.com/2008/05/php-rand01-on-windows-openssl-rand-on.html">This one</a> is also pretty cool and worth a read IMO).
I wanted to give this a try, and I made a generator for this as well.  


<img src="/random/randompng.php?xlen=256&ylen=256">


No immediately evident pattern, which is good.  I'm sure there is a pattern at some level though.


I  made a colored version too:


<img src="/random/randompng.php?color=1&xlen=256&ylen=256">


It is definitely a lot slower to generate than the B&W version.

I'll keep improving this generator, and adding new random stuff as it comes to me or as I want to fiddle with it.  
Plus I'm sure my wife will have suggestions once she uses it some.

Oh, and naturally the source code for all of this random stuff is available on that page under the CC or whatever.  I'm just not liable for...anything. ;-)


Tags: #random #PRNG #PHP

 original filename: 163