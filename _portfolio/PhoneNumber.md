---
layout: post
title: Create A Phone Number using JS
thumbnail-path: "img/PhoneNumber.png"
short-description: Output a phone number after receiving an array of 10 integers using JavaScript.
---

**Summary/Problem** - 
Write a function that accepts an array of 10 integers (between 0 and 9), that returns a string of those numbers in the form of a phone number.



**Explanation/Problem**-
The objective of this problem is to create a function which will return an actual phone number when receiving an array of 10 numbers.  This phone number must be output as a string in standard telephone number format: (xxx)-xxx-xxxx.




**Solution**-
For this problem, like many others there are a few way to get to a solution.  My preferred method was to set my output format first.  I did so by declaring a variable for my output and setting it equal to the correct format, with x's as placeholders for my numbers.  The next thing that we needed to do was to go through the array one by one and output and replace the x with the actual number that we were cycling on at that interval.  Once we did this we are simply able to output the telephone number as the string has had the numbers plugged in properly.

{%highlight javascript%}
function createPhoneNumber(numbers){
  var output = "(xxx) xxx-xxxx"; //declare my output formatting
  
  for(var i = 0; i < numbers.length; i++) //cycle through all input numbers
  {
    output = output.replace('x', numbers[i]); //swap each number into output replacing the x's
  }
  
  return output; // display my phone number output
}
{%endhighlight%}

**Results/Conclusion**-
The result of this is that when we provide an array of 10 numbers to the function it will output an actual telephone number in standard format.  In conclusion, I realize that this is not some extravagant project, however it does show rational thinking.  In the world of development the most efficient way to get a job done is the best way to get the job done **WHILE MAINTAINING USABLITY**.  I think that this is best use case for this task and that is why I chose to showcase this piece of work.  I planned to showcase another version of BlocJams, however the only real difference would have been utilizing AngularJS and Jquery instead of just plain JavaScript and DOM. 