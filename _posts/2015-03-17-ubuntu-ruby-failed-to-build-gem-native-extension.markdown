---
layout: post
title:  "How to overcome the \"Failed to build gem native extension\" error"
date:   2015-03-17 15:30:01
---
This is my first dev log post. I had decided to blog about my dev-pangs.
Here is the first roadblock that I encountered since I started this Dev Log.This week our team at [Freshdesk][freshdesk_url] got a brand new Dell Workstation(Intel Xeon 3.30GHzx4 , 16GB and a 1080p 21.5" LED monitor). It runs two OSes Windows 8.1 and Ubuntu 14.04. This got me excited!!

I've been using a Mac for the past 10 months and got pretty comfortable with the environment, but still good old ubuntu made me feel at home.

The first ```apt-get``` that I fired was to install ruby on Ubuntu : ```sudo apt-get install ruby ``` and it worked like a charm, thanks to our thrifty ```apt-get```

For Rubydevs [Gems][rubygems_url] are apples in our eyes. The first gem that I tried to install was the ```mysql``` gem. I did a ```sudo gem install mysql``` and this threw out the following error:

```Error installing mysql:
	ERROR: Failed to build gem native extension.```
  {% highlight bash %}

  ERROR:  Error installing mysql:
	ERROR: Failed to build gem native extension.

        /usr/bin/ruby1.9.1 extconf.rb
/usr/lib/ruby/1.9.1/rubygems/custom_require.rb:36:in `require': cannot load such file -- mkmf (LoadError)
	from /usr/lib/ruby/1.9.1/rubygems/custom_require.rb:36:in `require'
	from extconf.rb:5:in `<main>'


Gem files will remain installed in /var/lib/gems/1.9.1/gems/mysql-2.9.1 for inspection.
Results logged to /var/lib/gems/1.9.1/gems/mysql-2.9.1/ext/mysql_api/gem_make.out


  {% endhighlight %}


Ruby and Rails are especially infamous for such dependency issues and I was in the middle of one this time! The scripts that run on the Mac would not run in the Linux machine as gems could not be insatlled!

**However doing a ```apt-get install ruby-dev``` would solve the ```ERROR: Failed to build gem native extension``` error.**

I faced these errors while trying to install mysql and nokogiri gems, however the rest_client gem got installed just fine!

Adios! niños y niñas! Gracias!









[freshdesk_url]: https://freshdesk.com
[rubygems_url]: https://rubygems.org
