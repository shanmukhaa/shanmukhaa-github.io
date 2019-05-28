---
layout: post
title: "Delay startup of app in Elementary OS"
modified: 2014-10-13T20:17:12+02:00
excerpt: "Sometimes it is useful to launch an app after wifi has connected"
tags: [Elementary OS, Linux, Bash ]
comments: true
---

When you use an app almost all the time, you usually want to add it to your list of start up item, to make them start up automatically. However for some apps, like browsers, it opening the app before an Internet connection is established will result in failed page/app loads. Therefore it is nice to know how to delay the start up. This post will focus on [Elementary OS](http://elementaryos.org/), but a similar approach should work in other Ubuntu variants. I will use Google Chrome as an example.

First, open your favorite text editor and paste the following

{% highlight bash %}
#!/bin/bash
sleep 10
google-chrome
{% endhighlight %}

Save the file somewhere on your hard-drive and name it `chrome_launch.sh`. 

Next you need to make the script executable. To do that run the following from the terminal:

{% highlight bash %}
 chmod +x [path to file]/chrome_launch.sh
{% endhighlight %}

The Open `system settings -> Startup Applications`. Press `Add` and in the `Command` field, navigate to your bash script. Then at the beginning of your path add `sh`, to tell the terminal to execute the script. 

If you want, you can also add a name and a description. 

{% highlight bash %}
sh [path to file]/chrome_launch.sh
{% endhighlight %}

My setup looks like this:
<br/><br/>
![Chrome startup with delay](../images/posts/chrome_dealy.png "Chrome startup with delay")
<br/><br/>

Chrome will now launch with a 10 second delay. This will be enough for the wifi to connect before chrome launches. 