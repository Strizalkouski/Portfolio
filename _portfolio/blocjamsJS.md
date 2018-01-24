---
layout: post
title: BlocJams Angular
thumbnail-path: "img/BlocJamsJS.png"
short-description: BlocJams is a Spotify like music player built with JavaScript!
---
{:.center}
![]({{ site.baseurl }}/img/BlocJamJSPlayer.png)

**Summary** - 
The objective of designing and developing BlocJams was to create a Spotify-esque platform.  This project features an obvious landing page - complete with responsive design, A collection view so that you can view different albums, an album view which will contain all of your songs on any given album, as well as a music player.  BlocJams comes complete with seek, skip, previous, and pause functionality - so it's ready to pump up the volume and provide enjoyment!




**Explanation** - 
The sole purpose of BlocJams was to create a true to life music player experience.  With BlocJams you can browse music, choose your songs, and listen at your leisure.  While working on the project - similar to the real world - you want to make sure you take mobible users and different screen sizes into consideration.  BlocJams is fully responsive and will adapt well for mobile users and desktop users alike.  BlocJams was put together using basic JavaScript as well as some DOM manipulation.  There are also a few quality of life features such as feature points not showing until scrolled to on certain screen sizes.  Once they are scrolled into view they will use a fading in transition for aesthetics.  




**Problem** -
The problem with creating something of this type is really bringing it all together, making it aesthetically pleasing, and having functionality at the same time.  Some of the problems which arose during creation are *time codes , formatting seek bars and volume bars ,  calculating fill percentage after thumbs move , programming logic for play/pause button visiblity*.




**Solution** - 
I would like to showcase some solutions for the above problems here.  Starting with my timecode filter: 
{% highlight javascript %}
var filterTimeCode = function(timeInSeconds){
  //use parseFloat method to get the seconds in numberpa
  timeInSeconds = parseFloat(timeInSeconds);
  var minutes = Math.floor(timeInSeconds/60);
  //store variable for whole seconds and whole minutes using math.floor to round down
  var seconds = Math.floor(timeInSeconds%60);
  //return the time in X:XX format
  if (seconds < 10){
    return (minutes + ":0" + seconds);
  }
  else{
  return (minutes + ":" + seconds);
  }
}
{% endhighlight %}

First we went ahead and filtered the time down to the nearest whole second. then using that number we aquired our minutes by using Math.floor and dividing the total seconds by 60 to find how many minutes there are.  Once that is done we set up the format for time which is X:XX, while planning ahead for the fact that before 10 seconds you need to have a 0 placeholder.

Figuring out how far to fill a seek bar especially when taking into account the placement of the thumb-slider is a bit more complex:

{% highlight javascript %}
var updateSeekPercentage = function($seekBar, seekBarFillRatio){
  //Check 21 Multiply by 100 to find a percentage
  var offsetXPercent = seekBarFillRatio * 100;
  //Check 21 Makes sure our percentage cannot be Less than 0 and no more than 100
  offsetXPercent = Math.max(0, offsetXPercent);
  offsetXPercent = Math.min(100, offsetXPercent);
  //Check 21 convert our percentage to a string and add % to end, then set the width of the .fill and the left value of the .thumb class - CSS interprets the value as a percent instead of a unit-less number between 0-100
  var percentageString = offsetXPercent + '%';
  $seekBar.find('.fill').width(percentageString);
  $seekBar.find('.thumb').css({left: percentageString});
};
{% endhighlight %}

Above we first multiply the seek fill ratio by 100 to convert it to a percentage.  After that we set our minimum of 0 and maxiumum of 100 so we cannot seek **outside** of the bars.  After that we convert to a string before finally finding the fill percentages based on the width.  The css interprets the value as a percent instead of a unitless number between 0-100.  After this is complete, our fill is able to be accurately calculated.



**Result and Conclusion** -
The result when we put everything together is a functional, and reusable music client.  This client currently is setup using static music, meaning local folders.  It can be paired up with backend functionality in the future however to create a music player or audio player for other needs.  BlocJams has everything implemented in it that you would want in a basic player, and this is a great foundation for a larger project in the future.  I intend to utilize the basic functionality of BlocJams in the future for websites or applications that need not only music but possibly tutorial audio or other basic instructional learning material.
