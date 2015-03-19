---
layout: post
title: "How to read CSV files in Ruby the smart way"
date:   2015-03-19 15:30:01
---

As a guy involved in data migration, CSVs are an integral part of my life. They are my favorite file format too. People might argue that using another flat format like XML,YML,ZML(just kidding) etc is definitely better. My friend and colleague [Kiran Gowtham](https://in.linkedin.com/pub/kiran-gowtham/20/a84/144/en) and I had even gotten into catfights over using a CSV vs using an RDBMS. I do agree that using an **RDBMS gives us more control, however sometimes all that we need is just a plain text file**. Using an RDBMS like mysql might be an overkill.


I am going to stop pitching for flat-files and let us get into reading an actual CSV File. Mostly the CSVs that I deal with are generated from spreadsheets or database tables.


####Consider the following CSV structure:

  _people.csv_

{% highlight text  %}

Name,age,hometown
Aswin,22,Madurai
William,35,Birmingham
Henry,27,Chicago

{% endhighlight %}


You might wonder why reading a file that contains just plain text draws so much hype from my side. Of-course! reading a file is easy in any programming language and it is really simple in Ruby. Let us say **I want to read the CSV files and display just the hometown of people**, then I can use the following syntax to get it done in Ruby

{% highlight ruby  %}

file_handle = File.open('people.csv')

file_handle.each do |row|

  elements=row.split(',')
  puts "Hometown: #{elements[2]}"


end

{% endhighlight %}


Using the elements array we will be access elements in each line, one line at a time. Easy right?! The output of the above code would be
{% highlight text  %}
Hometown: Madurai
Hometown: Birmingham
Hometown: Chicago
{% endhighlight %}


But here comes the twist in the tale, consider the following file:

_people.csv_

{% highlight text  %}
Name,age,hometown
Aswin,22,"Madurai,India"
William,35,"Birmingham,UK"
Henry,27,"Chicago,IL"
{% endhighlight %}


If we run the ruby code that is shown above on people.csv, the output would be:

{% highlight text  %}
Hometown: India
Hometown: UK
Hometown: IL

{% endhighlight %}

As you can see splitting the string with the ',' does not give us the intended results. We will definitely face issues if commas are present within the fields.

We can programmatically solve this problem, however it might be something akin to reinventing the wheel given the fact that ruby comes with the powerful csv gem by default.

To use the ruby csv gem all we need to do is type ``` include 'csv' ``` in our ```.rb``` files.

Now take a look at this code with the CSV gem included


{% highlight ruby %}

require 'csv'

lines = CSV.read('people.csv')
#The CSV.read('people.csv') converts the people.csv into a 2D array

lines.each do |line|

  puts "Hometown: #{line[2]}"

end

{% endhighlight %}


The Output of the code would be:

{% highlight text  %}
Hometown: Madurai,India
Hometown: Birmingham,UK
Hometown: Chicago,IL

{% endhighlight %}


Thus the CSV gem saves the day!
