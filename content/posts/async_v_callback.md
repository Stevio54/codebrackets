---
title: "Async vs Callback"
date: 2017-10-09T19:15:18-07:00
tags: [cloud programmer,async,callback,promise,node,js,typescript,whoami,about]
image:
  feature: "/images/clouds.jpg"
  headimage: "/images/CloudIdeas.png"
draft: true
---

## The Story

### Hello Everyone!

While working with a good friend on some Node JS code we ran into an interesting issue. Do we use **async...await** in our code or make use of the **promise..callback** model when we pull data from another server?

In this case, he had already been writing the code using the **async...await** model but had been running into runtime errors with his code.

I looked at the code he was using, and the symptoms, and I saw that, in this case, his runtime environment and/or platform did not seem like the use of the &quot; **async**&quot; keyword.

For example:
```javascript
 
 module.exports=async (req, callback) =&gt; {
 
    letresult=awaitrequestpromise(opts);
 
    callback(null, result);

 };
 
```
Gave the error:

```javascript
 
 module.exports = async (req, callback) =&gt; ...                       ^

 SyntaxError: Unexpected token (

     at createScript (vm.js:56:10)
 
```

I suggested to him that he instead make use of the **promise..callback** model to accomplish the task.

Here is the code after a rewrite:

```javascript
 
 module.exports= (req, callback) =&gt; {

    request(opts)

        .then((result) =&gt; {

            callback(null, result);

    });

 };
 
 ```
Thankfully, the error did not repeat and his code worked as it was intended!

## Takeaways and things learned

What I take away from this experience, is that there are always multiple ways to accomplish any one task.

In this case, the issue was that the framework he was using had ran on an older version of NodeJS in which **async...await** was not available as a feature. Your situation may vary, but the solution will always be the same…

> **Never get stuck in a corner, the programming toolbox is full of wonders!**

To illustrate this further, it can be noted that another solution for this situation would be to switch from JavaScript in node to Typescript (a story for another day...). 

#### Do you have another way you would approach this problem in your code? Please write me a comment, I would love to hear from you!

Cheers!

Steven