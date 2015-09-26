---
layout: post
title: Feature Detectors in Machine Learning
---

Before we dive into feature detectors, let's review what machine learing is and why it's important.

Computers are not much more than really fast calculators.  Everything you on your laptop or phone is, at a fundamental level, a really fast and complicated math problem.

A picture, for instance, is simply thousands of pixels, with each pixel having three colors, and each color having a brightness value between 0 and 255.  It is a very big number, but that's all it really is.  A YouTube video would be just a bunch of pictures strung together with even more for audio.

So, computers are great at math as well as displaying media.  However, the computer itself has no idea what is in those pictures, as it is just doing the math.  A computer can store all the information on Wikipedia, but has no idea what any of it means.

Imagine giving a picture to a computer and asking it, 'Is there an apple in this picture?'  How could you design a math problem to understand what sequence of numbers represents an apple?

That's where feature detectors some in.

Let's try something a bit easier first.

We can create a program that takes handwritten numbers 0-9 and guesses which number is written.  For simplicity, lets say the numbers are written in a 30-by-30 grid of pixels.

You could try to program each pixel manually, but there is a better way.

Why don't we give voting rights to each pixel, and set each pixel to vote evenly between all possible answers: 0,1,2,3,4,5,6,7,8,9.

Then we can start showing it handwritten digits along with their correct results.  Each time you show the program a new digit, each pixel changes the amount it votes ever so sligthly toward the correct direction.  So, if the pixel was black and the number was 9, it will vote a little more for 9s the next time it's black.

We then go thru a training process.  We show the program thousands of pictures 