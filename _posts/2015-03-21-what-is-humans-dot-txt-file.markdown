---
layout: post
title: "What is humans.txt ?"
date:   2015-03-21 18:30:01
---
We all would have seen the [robots.txt](http://en.wikipedia.org/wiki/Robots_exclusion_standard) file in various websites. It is a file that specifies how automated website crawlers should behave in that particular web domain. The file may ask the crawlers not to get into certain parts of the webpage or not get into the website at all! If it is traffic rules for vehicles on roads, it is the ```robots.txt``` file for crawlers and websites.

####**Why do we need a humans.txt file?**

![humans.txt logo]({{ site.url }}/assets/post-humans-txt/logo-humans.png)

Lately the web is full of computer generated content and in the age of machine learning human generated content is belittled. For instance two decades ago the postal service used to have handwritten letters and greeting cards oozing affection and emotions, but today most of the letters delivered by our postal service is computer generated printouts. In this age of driverless cars we need to remember that all the software, bots and tools are of the humans by the humans for the humans. To honor the humans who are behind these amazing tools, websites and software a humans.txt file can be included.

The trend of having a humans.txt file gained traction with the launch of [http://humanstxt.org](http://humanstxt.org) - a website that maintains the standards for the humans.txt file. Today I have implemented a [humans.txt file for this site]({{ site.url }}/humans.txt) on this site, you can see a small icon in the footer.

A humans.txt file can contain data about the people who power a site like the web developer, web designer, UI designer, marketing people, well wishers etc and their personal details. We can also include the tech stack and any other details that we wish to show people. Even [google has a humans.txt file](http://www.google.com/humans.txt).

The standard for humans.txt is very basic, topic headings should be in between /\* and \*/ and information should be in key: value format, however it is not absolutely necessary to adhere to this format.

####**Here is the humans.txt file's content of this site:**

{% highlight text  %}

/* TEAM */
        Devlogger: Aswin Vayiravan
        Twitter: @123aswin123
        Github: 123aswin123
        From: Madurai(♡), India

/* THANKS */
        Mom: Sudha Annamalai
        From: Madurai, India

        other_people=["Puss","Doggie","God"]


/* SITE */
        Language: English
        Doctype:HTML5
        Tools: OS X,Atom,Markdown,HTML,CSS,Jekyll,Github pages

{% endhighlight %}

Once I implement a robots.txt file for this site, I shall Jekyll about it, until then Hasta la vista!
