---
layout: post
title:      "Quick Basics of Redux"
date:       2018-08-10 14:53:27 +0000
permalink:  quick_basics_of_redux
---


If you’re like me, you started to learn a little bit of ReactJS and think, “not bad.” Then you found out that there were better ways to handle a component’s state. Seems easy enough, right? Enter Redux! At first, the concepts of the store, reducers, and actions make a good amount of sense. All of these pieces of the puzzle are, more or less, fairly basic JS functions. However, when it was time to put all of these puzzle pieces together, I was absolutely lost. *So you have to call ```createStore()``` with a reducer argument, creating a new store object, which then uses a dispatch method to accept an action function that returns a JS object, with an action name and a payload, to trigger a specific return value in said reducer*. Phew! I even got a little confused just by typing that sentence. There seems to be a lot of moving parts and even more boilerplate just to avoid using a simple method like ```this.setState()``` which seems to be a little counterintuitive considering we have been trained to simplify our code. 

Today I hope to explain and simplify the basic pieces of the Redux puzzle. I promise, that once you understand each piece and how they all come together to return the desired state it will be quite easy to implement Redux into a simple React application. 

**The Store, Reducer, and Actions**

First off, your application will have to be placed within a “Provider” component, which must be imported from the React-Redux library. This component will accept the store as a prop, as seen below.

```
<Provider store={store}>
    <App/>
</Provider>
```

But what is this “store” you ask? Putting it simply, the store is just a JS object. The ```createStore``` function just creates a new object that contains just the state and four methods: ```getState```, ```dispatch```, ```subscribe```, and ```replaceReducer```. (For the sake of this article we will only discuss state, getState and dispatch.) The example below illustrates how a store is created.

```
const new_store = createStore(reducer)
```

However, before we talk about any of these methods, we must talk about the reducer. The reducer works like a switchboard, and will react a certain way, when it receives a certain action as an argument. The reducer, upon triggering said action, will return some version, or copy, of the store’s state. It seems like there is a lot of stuff going on here … and that’s because there is!

Lets look at an example:

```
// state (usually an object but we’ll use an integer for the sake of this example)
const state = 1

// an action, usually saved as a string describing said action
const plus_one = “PLUS_ONE”

// reducer function
function reducer(state, action){
    switch (action) {
	case “PLUS_ONE”:
	    return state + 1
	case”MINUS_ONE”:
	    return state - 1
 	default:
	    return state
    }	
}

reducer(state, plus_one) // output: 2

```

Thats pretty much what happens inside of the store when you want to call a specific action, but how do you bring all of these pieces together? Well, if you look back to the second snippet of code in this article, our store contains a reducer as soon as it is created. The ```createStore``` function must be given a reducer as an argument, so that the reducer exists within your store. There is a caveat, however. Instead of just calling store.state or store.reducer, there are different ways to access these “hidden” values/methods.

Firstly, upon its creation, there is a “state” value that is managed by the store and is only available by calling ```getState()```. Your best bet is to make sure that whenever you set a state, it is a JS object, so it can be easily converted to JSON.

Now, whenever you want to make a change to your application’s state, you must use the ```dispatch``` method. This method sends an action to the state’s reducer. For the purposes of simplification, I would say to think of ```store.dispatch()``` as being basically equivalent to what you would expect ```store.reducer()``` to be. That being said, dispatch will accept and action which will trigger a specific block of code as shown in the example above. 

When it comes to “actions” they are little more straightforward, especially before middleware like “thunk” comes into play. As a convention, an action will be an object with two essential properties: ```type``` and ```payload```. The type will usually be a string that triggers a specific action in the switch statement as demonstrated in the example shown earlier. The payload will usually be data that will somehow interact with the state.

So hopefully, this brief breakdown of the basics will be helpful in establishing the foundation of your Redux knowledge. Once you have a solid understanding of how these pieces interact with one another, it will be a HUGE help when utilizing more advanced Redux techniques, such as the middleware mentioned above. Mainly, just don’t get discouraged. As with most of the coding skills that you have learned thus far, it seems way more difficult than it turns out to be. Now go and create the tiniest React application that you can and manage its state with Redux. It will take you less than an hour to set up and everything will make a lot more sense once you do! Happy coding!


