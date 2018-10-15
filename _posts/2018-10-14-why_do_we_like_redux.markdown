---
layout: post
title:      "Why Do We Like Redux?"
date:       2018-10-15 01:04:21 +0000
permalink:  why_do_we_like_redux
---


Redux and React. They seem to go together like peanut butter and jelly … but why? Why does our industry insist on managing state, and more specifically, why with Redux? Isn’t it just easier to manage state locally within a React application’s components? Well yes — but, no. It really depends on the size of your application. If you have a tiny React application that only has one or two container components with minimal state properties, chances are you’d be better off doing it the old fashioned way. However, what happens when you have several container components and even more stateless components? Things can get tangled up really quickly.

I wanted to experience this for myself. So, while working on my current project (a restaurant POS using React and a Rails backend), I chose to hold off on implementing Redux for as long as possible. At first, I didn’t miss it at all. I only had one container component, and although the local state object kept growing, it was relatively easy to work with. Immediately I thought, “See? Redux is overrated and just not worth all of the boilerplate involved in setting it up.” 

Fast forward a few weeks, to where my little POS project has grown and I want to keep adding features. Currently, I have 5 container components and I am already getting into trouble with state. It’s not that my application doesn’t work correctly, because so far it does (knock on wood). The issue now is that I am feeling a little disorganized and am getting dizzy trying to sort through different fetch calls and state changes throughout different components. Even more importantly, I need my state to be more centralized and certain properties must be accessed by several different components in different sections of my application.

Having your state equally accesible to all of your components is kind of magical if you think about it. You can spend *way* less time worrying about component relationships and passing props and think more logically about how you want to setup your application. It doesn't take long to realize how much of a pain it can be to pass props two or three components deep; things can sloppy rather quickly.

Currently, I am working to properly implement Redux before I continue adding onto this side project of mine. My last project was considerably smaller and adding Redux at the end was a breeze. Unfortunately, this will not be the case with my larger POS app. So here's my final tip: **add Redux at the beginning** if you know that your project will be more than just a few components, it'll save you from rewiring a lot of functions! 
