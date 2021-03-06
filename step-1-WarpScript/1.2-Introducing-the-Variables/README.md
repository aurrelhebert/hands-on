# Step-1.2: Introducing WarpScript Variables!

## Variables

As any other programming language, WarpScript implements the Variables concept. In WarpScript you can save a specific stack element in a variable (java pointer). This is done using the function [STORE](http://www.warp10.io/reference/functions/function_STORE/). 

This function expects two elements on the stack : 
- A stack element to save
- A variable name

Then to push back the element on the stack, write the variable name **precede of a $**.

Let's try it, save the following string in a variable and then push it back several time on the stack!

```
// A WarpScript string
'Hello World!'

// Save this string in variable


// Play with the saved variable


```

## Get a read token

Security in Warp10 instance are handled with crypto tokens. They can be pretty long, so to ease your workflow, we stored it in the platform! You can push the token into the stack using this:

```
@HELLOEXOWORLD/GETREADTOKEN
```

You can store it in a variable if you want.

# To be continued

Great job! Let's continue with some WarpScript list manipulation in the [next step](/step-1-WarpScript/1.3-Manipulate-a-data-list/README.md).