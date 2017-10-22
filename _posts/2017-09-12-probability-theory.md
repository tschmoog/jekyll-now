---
published: false
---
## Probably the best starting point

Where to start? The intention of this blog is to smooth out the the niggles of machine learning and make it as acessible to those with limited technical and mathematical experience or ability. That being said, the field of ML/AI was birthed through a combination of engineering, computer science and statistics and so one must understand the fundamentals before moving on to understand the more attractive and exiciting ideas. Because of this, I feel probability theory (alongside decision theory and information theory) is as good a place to start as any. 

Ingredients:
A decent grasp of linear algebra and calculus.

### Why do we need probability theory?

All data is obtained through observation and measurement. This means noise will bleed in to the data, be it through the data not being entirely accurate or representative of a population, potenitally due to bias or an insufficient quanitiy, or through the instruments by which measurements are made having a degree of uncertainty or error. Because of this, data is useful to discover _trends_, however it is good to assume there is a degree of inaccuracy or variability within the data, which hopefully can be accounted for when the data is looked at in aggregate. Probability theory gives us the framework to express this uncertainty in a precise and quantitative manner.

### A simple example:

Imagine two bags,filled with black and white marbles.  Bag 1 contains 10 marbles, 4 black and 6 white, and bag 2 contains 6 marbles, 5 black and 1 white.

*diagram*

Let us remove marbles from each bag, inspect their colour and return them to the bag they were taken from. We inspect items from bag 1 20% of the time and bag 2 80% of the time. In this instance the bag which we choose to take a marble from is a variable $$B$$. $$B$$ can take one of two values, bag 1 or 2. The marble removed is also a variable that can take on two values, we can denote the marble varialbe as $$M$$ and it's resulting colour black ($$b$$) or white ($$w$$). 

We can measure a probability as the number of times an event occurs out of the number of trials. Assuming we pick bags and marbles an infinite number of times, we can see that the probability of picking bag 1 is 1/5 and bag 2 is 4/5. We can write this mathematically as:

$$p(B=bag1) = 1/5 = 0.2$$

$$p(B=bag2) = 4/5 = 0.8$$

Given this information we can now ask questions and make inferences foward such as:

"What is the overall probability we will pick a black marble on the next selection"

or backwards:

"Given I'm holding a black marble, what is the probability it came from bag 1"

These questions and more complicated ones can be answered using the sum rule and product rule, two rules in probability which we will derive below:

Imagining two random variables, $$X$$ and $$Y$$. Supposing variable $$X$$ can take any value $$x_{i}$$ ($$i=1,............,M$$) and $$Y$$  can take any value $$y_{j}$$  ($$j=1,............,M$$). Presuming $$N$$ number of trials (for simplicity we will imply $$N\rightarrow \infty$$ ). Let the number of trials where $$X = x_{i}$$ and $$Y = y_{j}$$ be $$n_{ij}$$.

Finally, let the number of trials where $$X = x_{i}$$ (irresepctive of the $$Y$$ value) be $$c_{i}$$ and the same for $$Y$$ values $$Y = y_{i}$$ be $$r_{j}$$.

The probability of $$X = x_{i}$$ and $$Y = y_{i}$$ can be mathematically denoted as: 

$$p\left ( X = x_{i},Y = y_{j} \right )$$

This is the joint probabiliy, and is the probability of two (or more) events occuring. As earlier, this probability is the likleyhood of both events occuring simeltaneously out of the total number of trials. 

Till this point we have been quite explicit about the values with which variables $$X$$ and $$Y$$ can take, however this was for the sake of explanation. For brevity and with apropiate context we can afford to be less pendandic and denote the sum and product rules as: 


Sum rule: $$p(X)= \sum_{Y}^{ } p(X,Y)$$

Product rule: $$p(X,Y)= p(Y|X)p(X)$$

These two rules form the basis for a lot of probabilitstic work in machine learning. 

## Bayes' Theorem 

Using the symmetry $$p(X,Y) = p(Y,X)$$ and the produc rule above, we can deduce the following relationship between probabilities which is known as _Bayes theorm_ which plays a large role in machine learning. 

$$p(Y|X) = \frac{p(X|Y)p(Y)}{p(X)}$$

Using the sum rule, we can expand the denominator and express it in terms of the numerator as:

$$p(X) = \sum_{Y}^{ }p(X|Y)p(Y)$$

This denominator is useful as is ensures that all our probability values over the range of $$Y$$ sum to 1. 

Returning to our original example of marbles and bags we can now express the problem mathematically as follows:

The probability of selecting either bag as mentioned earlier:

$$p(B=bag1) = 1/5 = 0.2$$

$$p(B=bag2) = 4/5 = 0.8$$

And the probabilities of selecting a specific colour marble, given a bag are:

$$p(M = b|B=bag1) = 4/10 = 0.4$$

$$p(M = w|B=bag1) = 6/10 = 0.6$$

$$p(M = b|B=bag2) = 5/6 = 0.8\dot{3} $$

$$p(M = w|B=bag2) = 1/6 = 0.1\dot{6}$$

We can use the earlier derived rules to then evaluate the total probability of say, ending up with a white marble

$$p(M = w) = p(M=w|B=bag1)p(B=bag1) + p(M=w|B=bag2)p(B=bag2)$$

$$ = 0.4 * 0.2  + 0.1\dot{6} * 0.8 = 0.21\dot{3} $$

from here we can conclude the probability of a black marble $$= 1-0.21\dot{3} = 0.78\dot{6}$$

More interestingly, we can infer information, say we are given a black marble and we would like to work out what bag it came from, Bayes’ theorem can be used to work out the probability of a specific bag, starting with bag 1:

$$p(B=bag1|M=w) = \frac{p(M=w|B=bag1)p(B=bag1)}{p(M=w)}$$

$$ = \frac{0.6* 0.2}{0.78\dot{6}} = 0.15 $$ to 2 decimal places. 
 Perhaps unsurprisingly given a black marble we can see that there is a 15% probability of it coming from bag 1 and a 85% probability of it coming from bag 2. While this does __not__ tell us which bag the marble _actually_ came from, it gives us an estimate and the best choice to take should we have to guess which back it came from, allowing us to make decisions or take actions based on uncertain information. 

This is a simple first step into probability, which will be expanded on in future posts. 
