---
published: true
---
## Probably the best starting point

Where to start? The intention of this blog is to smooth out the the niggles of machine learning and make it as acessible to those with limited technical and mathematical experience or ability. That being said, the field of ML/AI was birthed through a combination of engineering, computer science and statistics and so one must understand the fundamentals before moving on to understand the more attractive and exiciting ideas. Because of this, I feel probability theory (alongside decision theory and information theory) is as good a place to start as any. 

Ingredients:
A decent grasp of linear algebra and calculus.

### Why do we need probability theory?

All data is obtained through observation and measurement. This means noise will bleed in to the data, be it through the data not being entirely accurate or representative of a population, potenitally due to bias or an insufficient quanitiy, or through the instruments by which measurements are made having a degree of uncertainty or error. Because of this, data is useful to discover __trends__, however it is good to assume there is a degree of inaccuracy or variability within the data, which hopefully can be accounted for when the data is looked at in aggregate. Probability theory gives us the framework to express this uncertainty in a precise and quantitative manner.

### A simple example:

Imagine two bags,filled with black and white marbles.  Bag 1 contains 10 marbles, 4 black and 6 white, and bag 2 contains 6 marbles, 5 black and 1 white.

*diagram*

Let us remove marbles from each bag, inspect their colour and return them to the bag they were taken from. We inspect items from bag 1 20% of the time and bag 2 80% of the time. In this instance the bag which we choose to take a marble from is a variable $$B$$. $$B$$ can take one of two values, bag 1 or 2. The marble removed is also a variable that can take on two values, we can denote the marble varialbe as $$M$$ and it's resulting colour black ($$b$$) or white $$(w)$$. 

We can measure a probability as the number of times an event occurs out of the number of trials. Assuming we pick bags and marbles an infinite number of times, we can see that the probability of picking bag 1 is 1/5 and bag 2 is 4/5. We can write this mathematically as:

$$p(B=bag1) = 1/5 = 0.2$$

$$p(B=bag2) = 4/5 = 0.8$$

Given this information we can now ask questions and make inferences foward such as:

"What is the overall probability we will pick a black marble on the next selection"

or backwards:

"Given I'm holding a black marble, what is the probability it came from bag 1"

These questions and more complicated ones can be answered using the sum rule and product rule, two rules in probability which we will derive below:

Imagining two random variables, *X* and *Y*. Supposing variable X can take any value xi (i=1............M) and Y  can take any value yj (same). Presuming N number of trials (for simplicity we will imply N -> infinity). Let the number of trials where X = xi and Y = yj be nij.

Finally, let the number of trials where X = xi (irresepctive of the Y value) be ci and the same for Y values Y = yi be rj.

The probability of X = xi and Y = yi can be mathematically denoted as: 

$$p\left ( X = x_{i},Y = y_{j} \right )$$

This is the joint probabiliy, and is the probability of two (or more) events occuring. As earlier, this probability is the likleyhood of both events occuring simeltaneously out of the total number of trials. 


Lots of latex below::::::::::::: 


Sum rule:

Product rule:
