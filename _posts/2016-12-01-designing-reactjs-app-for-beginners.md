---
layout: post
title: Designing ReactJS App for beginners
tags: ruby rails
---

Almost every guy working in tech has heard about [ReactJS](https://facebook.github.io/react/) by now. Some might even know [Redux](http://redux.js.org/), [Flux](https://facebook.github.io/flux/) and something better. In this article I’ll be focusing on problems that I, as a beginner faced with ReactJS and what I learned from them.    

Since I learnt programming, I don’t know why, but I always tried to run away from javascript. Not because I hate it. but because I had (only) heard of a billion javascript frameworks, extensions, transpilers, package managers etc, which would stop me from knocking javascript’s door. Then I was first introduced to ReactJS at my workplace. At that time, I had a little (read as no) experience with any javascript. Yeah, I know Javascript is the ***key*** to the web development, (but hey, who are you to judge). It was all fine until I looked at ReactJS code and           

#### I Loved it ❤      

We use ReactJS with JSX syntax, so it really sped up my understanding process, since there were classes, constructors, extend keywords, which I was already familiar with. Things were great. I read the online documentation about ReactJS components, props & how to pass them to child components, states & how to set/use them. Now time had come to write down some lines of code. That’s when I faced       

## Beginner’s problems:


### Flow of execution
ReactJS has great execution flow. It first sets the initial values, then you can control what happens before first render, in the render, after the first render, things before and after the next renderings. But the same execution flow becomes very difficult to keep in mind, while designing your react UI for some time, till you get familiar with these calls.    

To overcome this, I thought of setting my wallpaper to the following image, which I was lazy enough not to create by myself (google image search to the rescue). Although this image does not show the complete flow, but was enough for a beginner like me. Looking at this few times per day, helped a lot.      


![](/assets/img/react-lifecycle.png)*Source : [Reddit](https://www.reddit.com/r/javascript/comments/45khex/reactjs_life_cycle_diagram_oc/)*

Although I was referring to this diagram and the (very well written) official documentation, I faced another problem.        

### Designing UI which involves multiple components
As soon as you start building your complex GUI, you start to think about what your design should look like. What components should be there, what data each one should hold and whether that data really needs to be in the state or would it better if it’s passed in the props. These questions will keep your mind more busy than actually writing the code.       

First thing you should do before writing your ReactJS code is read this. It is written by people who expect, how react should be used to get maximum from it. It was my misfortune, that I read this after I had already written some code. But it sure helped me to know where I was wrong and correct typical beginner mistakes. Now it has been more than 3 months and I thought to share what I learned from my past mistakes, which you should avoid while using ReactJS.


1. Keep your components simple. 
2. While writing a component, make them as generic as possible so that you follow DRY (Do not Repeat Yourself). And use the same component at different use cases.
3. When you need to store state into parent of a component, make sure the other children of that parent should also need that change. If not create a separate parent component for that specific component.
4. Avoid unnecessary renders. Above points tries to implement the same. This is required, if the unnecessary rendering is going to cost you some resources (API Calls/Computations). This in turns also tries to reduce page load time.
5. Try avoiding storing states in child components. Try to use props as much as possible.
6. Use browser debugging to verify, if all the render calls are happening as expected.        

That's all folks.
