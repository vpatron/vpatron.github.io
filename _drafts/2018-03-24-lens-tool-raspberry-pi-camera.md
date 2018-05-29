---
layout: post
title:  ""
date:   2018-03-24
banner_image: pi-nixie.jpg
tags: [raspberry pi, camera]
comments: false
---

The Raspberry Pi camera can only focus as close as maybe 0.5 meter (1.5 
feet). What if you want to go closer?

There's a much easier way than using an external macro lens: turn the 
lens to adjust close-in focus for macro shots. 

Here's a very simple way to make make a lens tool to easily focus the 
lens without scratching it.

<!--more-->

## Why a lens focus tool?

May people use pliers to adjust the focus, but one slip and your lens 
will be scratched and images will be quite dim (it's happened to me).

## Polymer modeling clay

The easy way is to use modeling clay. You form it and then bake it in 
your home oven to harden it. 

They sell inexpensive "polymer" types in craft stores, such as these:

{% include image_caption.html imageurl="/images/posts/FIMO-modeling-clay.jpg" title="FIMO modeling clay" caption="FIMO modeling clay" %}

## Steps to make the lens focus tool

1. Cut part of the protective plastic that you would normally peel off. 
   
   Cut only the part that is sticking out! LEAVE THE SMALL PORTION COVERING
   THE LENS ON to prevent clay from sticking to it.

   {% include image_caption.html imageurl="/images/posts/pi_zero_camera_with_protective_plastic.jpg" title="Raspberry Pi Zero camera" caption="Raspberry Pi Zero camera" %}

1. Cut a small piece of the clay, form it, and then squish it into the 
   camera lens.
   
   ONLY PRESS TO GET THE ROUND PART OF THE LENS. Do not press so much that
   you include the square body of the camera.

   The result should look like this:


   {% include image_caption.html imageurl="/images/posts/raspberry-pi-camera-lens-tool-pressing-clay.jpg" title="Press clay into camera" caption="Press clay into camera" %}

   {% include image_caption.html imageurl="/images/posts/raspberry-pi-camera-lens-tool.jpg" title="Raspberry Pi Camera Lens Tool" caption="Raspberry Pi Camera Lens Tool" %}

1. Harden the clay

   Bake the clay in an oven (a toaster oven will do) at the temperature 
   for the time recommended on the package instructions to harden it.
   Let it cool off before touching it.
   
And there you have it! A simple and useful tool that works every time
to focus your Raspberry Pi camera.

## Example images, with and without refocusing


{% if page.comments %}
<div id="disqus_thread"></div>
<script>

/**
*  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
*  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables*/
/*
var disqus_config = function () {
this.page.url = http://vince.patronweb.com;
this.page.identifier = pi_camera_lens_tool;
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
