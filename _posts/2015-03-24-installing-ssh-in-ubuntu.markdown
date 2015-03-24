---
layout: post
title: "SSH connect to host &lt;IP Address &gt; port 22: Connection refused - FIX"
date:   2015-03-24 18:30:01
---

We all love [ubuntu][ubuntu-url]. It is not only free as in free speech but also free as in free beer. It is a very popular linux distro that has prevented the market monopolization by giant corporations. Luckily I haveen assoiciated with ubuntu for the past 7 years.

SSH is one of those magical tools that lets users login to remote machines. When you perfrom a fresh install of ubuntu you will be able to SSH into other machines but SSHing into your machine is not supported out of the box. This is definitely a pain. Ubuntu comes literally tons of packages that we hardly use but it does not include a SSH server by default. Therefore it would be thrifty if Ubuntu shipped with SSH by default.

One of the biggest strengths of ubuntu is the 'Advanced Packagaing Tool' and the  ```apt-get``` command. We can install the the open ssh server by heading over to the Terminal and typing
{%highlight bash%}

sudo apt-get install openssh-server

{%endhighlight%} 

And Viola, you can SSH into your Ubuntu machine.




[ubuntu-url]: http://ubuntu.com
