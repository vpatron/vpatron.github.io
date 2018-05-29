---
layout: post
title:  "Driving a nixie module with a Raspberry Pi"
date:   2018-02-1
banner_image: pi-nixie.jpg
tags: [nixie, raspberry pi, python]
comments: false
---

A friend was poking around with these QS30-1 nixie modules from nixieclock.org. He mentioned that all the projects on the 'net used an Arduino but he really wanted to use a Raspberry Pi.

I looked at the Arduino code and Nixie board schematics and wrote a Python driver for it.

<!--more-->

## Why a Raspberry Pi?

Because a Pi is way more powerful: it is a computer running the Linux with wifi. This makes it controllable over a network or the internet with all the features and power of a full operating system. And a Raspberry Pi Zero W can be as cheap as an Arduino.

## Nixie module

This Python module was written using the QS30-1 from [nixieclock.org](http://www.nixieclock.org/?p=566) as a reference. This module is stackable for multipe digits and has an RGB LED backlight.
 
{% include image_caption.html imageurl="/images/posts/pi-nixie-qs30.jpg" title="QC30-1 Nixie module" caption="QC30-1 Nixie module" %}

I took a look at the schematic and found that it uses the old 74HC595 shift register to drive 16 outputs for each module. 10 outputs drive the nixie digits, 2 for the neon colon dots, and 3 for the RGB led which backlights each module.

The nifty thing is that these modules daisy chain so you can stack as many digits as you want together.

## Github

I posted the driver to [Github](https://github.com/vpatron0/pi_nixie) as open source software.

## How to use

I made it simple to use by embedding the backlight LED color and colon information as part of the text string you give it. A few examples will make it clear:

* Sending "b12:34" will display "12:34" with a blue backlight
* Sending "r1.2 g3.4" will display "1.2" in red, followed by a space, and then "3.4" in green. 

## Wiring

These modules require 4 pins for data transfer. The GPIO are "bit-banged" in software. Because no hardware resources are used (other than basic GPIO output function), any available GPIO on the Raspberry Pi can be used.

The line in the example below defines which GPIO pin is used for what function.

    nixie = pi_nixie.PiNixie(pinDATA=25, pinSHCP=23, pinSTCP=24, pinOE=18)

* pinDATA -- serial data for 74HC595
* pinSHCP -- 74HC595 shifts serial data on rising edge
* pinSTCP -- 74HC595 stores data on rising edge
* pinOE -- high turns on display and backlight, off turns off display and backlight

Note that pinOE is also used for adjusting the brightness of the digits and the backlight LEDs by PWM of the pinOE signal.

The numbers correspond to the GPIO number and not the actual pin number of the header connector. See the documentation for RPi.GPIO for details.

## Voltage Level Translator

The Raspberry Pi uses 3.3V logic, but the "Arduino compatible" Nixie modules use a 74HC595 shift register IC that is powered at 5V and, technically, should be driven with 5 Volt logic. 3.3 Volts does not meet the 74HC595 datasheet minimum for a logic "1" (Vih). However, in tested HW, it works fine.

If you want to meet all technical requirements for a very robust design, you can use a 3.3V to 5V level shifter such as a 74HC125.


I’ll try to help these Nixie and VFD (vacuum flourescent display) kit vendors make more products for the Raspberry Pi.


{% if page.comments %}
<div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
/*
var disqus_config = function () {
this.page.url = http://vince.patronweb.com;
this.page.identifier = pi_nixie;
};
*/
(function() { // DON'T EDIT BELOW THIS LINE
var d = document, s = d.createElement('script');
s.src = 'https://vince-patronweb.disqus.com/embed.js';
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
                            
{% endif %}
