# Step-3.3: Framework time: MAP!

The function used allow some small GTS manipulation but WarpScript offers other rich tools for manipulating the GTS. Five frameworks are available and they all have their specific usage and important place in Time-Series analytics: [FILTER](http://www.warp10.io/reference/frameworks/framework-filter/), [BUCKETIZE](http://www.warp10.io/reference/frameworks/framework-bucketize/), [MAP](http://www.warp10.io/reference/frameworks/framework-map/), [REDUCE](http://www.warp10.io/reference/frameworks/framework-reduce/) and [APPLY](http://www.warp10.io/reference/frameworks/framework-apply/). Let's end with the MAP framework.

***At the bottom of this page, you will find the instructions on how to process to apply a mapper on the NASA lightcurve data.***

## The framework

Now it is time to update the values of a set of GTS using the [MAP framework](http://www.warp10.io/reference/frameworks/framework-map/). The MAP framework allows you to apply a function on values of a Geo Time SeriesTM that fall into a sliding window.

![Alt Text](/assets/img/frameworks/mapper.png)

In other words, the MAP framework allows the user to compute the same operation on all the points of a series. For specific kind of operations (means, min, max...), some points directly before and after the current point can be added to the computation. This resume the concept of sliding window around each points.

## Input parameters

Map takes as input a list of parameters. The first element of this list can be one or several lists of GTS. Then there is a [mapper function](http://www.warp10.io/reference/#framework-mappers). The third and the fourth elements are related to the sliding window, with first an element corresponding to "pre", the width of the sliding window before the value, and in second an element corresponding to "post", the width of the sliding window after the value. The last element corresponds to "occurences" which is the limit of computation of a number. For all elements except the set of GTS and the mapper function a default value 0 can be used, when those elements aren't required.

```
// MAP Framework
[
    SWAP                                // Series list or Singleton
    mapper.function                     // Mapper function operator
    0                                   // Pre
    0                                   // Post
    0                                   // Occurence
]
MAP

```

**Pro tips: A mmapper with the pre, post and occurence parameters at zero is called a single value mapper, meaning that the mapper function will be applied to all points of a series!**

To get a working mapper, replace the function keyword by an exisiting function as replace, mean, min, max, sd, abs, mul, add, round...

## Mapper in pictures

Let's resume step by step each mapper element. First [MAP framework](http://www.warp10.io/reference/frameworks/framework-map/) requires a set of Time series (Singleton or list):

![Alt Text](/assets/img/frameworks/Time-series-input.png)

The second step consists to choose the function to apply on each points (resp window): replace, mean, min, max, sd, abs, mul, add, round and [lot of others](http://www.warp10.io/reference/reference/#mappers):

![Alt Text](/assets/img/frameworks/mapper-op.png)

A mapper can be tuned according to three parameters: pre which corresponds to the number of points to integrate to the sliding window **before** the current point:

![Alt Text](/assets/img/frameworks/mapper-pre.png)

The second parameter to tun a mapper consists of post: which corresponds to the number of points to integrate to the sliding window **after** the current point:

![Alt Text](/assets/img/frameworks/mapper-post.png)

And finally the last parameter used to tun a mapper is occurences which specify the maximal number of computation of each points!

![Alt Text](/assets/img/frameworks/mapper-occurences.png)

Now we would like to apply this specific framework to compute the same operation on all the Time series points of the NASA lightcurve data. Let's see how to process!

## Hello Exo World step

In previous step we saw how to downsample the data, but what if to get the main aspect of the lightcurve we would like now to compute its approximate trend? In statistics, we could compute a moving average as example. In WarpScript, the map framework can be used to approximate such a computation. For a example we can define a window containing 5 elements before and as many after the current point and compute its mean value.

Let's try it! Try the mapper.mean with a moving window!

```
// MAP Framework
[
                                        // Series list or Singleton
                                        // Mapper function operator
                                        // Pre
                                        // Post
                                        // Occurence
]
MAP

```

## Resume

The main goal of this step is to compute a moving average of some Time series. To do so, you used the MAP framework, it expects on top of the stack a list of parameters containing: the Time series as list or as singleton to bucketize, a mapper function, and three long parameter: pre, post and occurences.

The result of this step corresponds to a computed Time series list. In our case the 4 selected Time series are now on top of stack containing averaged value of all the values inside a moving window (for each point).

# To be continued

Congrats, you reached the end of the framework step! Understanding the help providing by those framework is really important to help a young hunter to complete its quest to retrieve Kepler-11 exoplanet. In the [next step](/step-4-First-Exo-Detection/4.1-Yet-another-framework-APPLY/README.md) we will focus, now that we have all the needed tools, on writing a working exploratory script to discover existing exoplanet for kepler-11!
