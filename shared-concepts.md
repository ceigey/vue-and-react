# Concepts

## Introduction

Vue and React are both JavaScript-based solutions for generating dynamic UIs in the user's browser.
Due to them solving a similar issue, they have a few similar concepts.

Here, we will explore some of those concepts,
and understand how much common ground Vue and React have for the developer who uses them.

_I won't try and explain all basic computer science terms, since those can quickly become rabbit holes!_


## Libraries and Frameworks

You might hear Vue and React called "Libraries" or "Frameworks" by different people.
I know the React team like to emphasise that React is a "library",
while the Vue team are perhaps not as fussed.

At this point, the main thing you need to keep in mind is that "framework" implies more of the broader problems
of creating a UI are addressed by a solution, while "library" implies that the solution only targets one problem area.

As such, the definition of these terms changes depending on the scale of the problem you are focussing on.
If we're thinking just about rendering, both Vue and React are frameworks.
If we're thinking about an entire application with different screens and widgets, neither are frameworks alone.

So I will call them __frameworks__ here.


## DOM

The [DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
(Document-Object Model) is a series of objects that represent the HTML document.

When using JavaScript without additional libraries, or jQuery, one updates the UI by:

* adding new elements
* selecting and modifying the properties of existing elements
* removing and replacing existing elements


## Components

Distinguishing Vue and React from writing dynamic UIs in Vanilla JavaScript and jQuery is the "Component" pattern.

The Component pattern involves the following:

1. Defining a __HTML template__
2. Specifying __data to display__ in the template
3. Using the template and data, __rendering some HTML__ onto the page
4. __Rerendering__ the HTML when data fed into the the template changes

_But why?_ Well, this helps us encapsulate our UI code,
so each Component is only responsible for a __pre-defined piece__ of the UI,
and there's less risk of confusing cross-over of code trying to update the same part of your webpage.

So, put simply:

* __Template__
* __Data__
* __Rerendering__

_So what does a component look like?_ Depends on your library:
React can have components written as both classes and functions,
while Vue components are wrapped in object literals. Looking at some examples is a good idea.


## Defining Components vs Rendering

Note that both Vue and React are doing two main things:

* Defining components
* Rendering them

Defining components is a formality - the developer needs to tell the renderer what the components
should be doing and what they should look like, and that needs to be done consistently.
So both Vue and React have a very opinionated idea about how to do that.

Rendering is actually a very deep process, and where the majority of a UI framework's work is done.
The renderer needs to render the components initially, track changes to data the components rely on,
and render the changes as efficiently as possible, so that the UI feels responsive to the end user.

Keep in mind Components can generally have other components nested inside of them, so the renderer might
have a lot of work it has to complete before it can even show UI changes.


## Lifecycles

Components have their behaviour when the template or data changes modelled as a __lifecycle__.

Following [the API for Vue](https://vuejs.org/v2/api/#Options-Lifecycle-Hooks),
a typical lifecycle addresses the following questions:

* Is the component about to be set-up by the renderer?
* Has the component been set-up by the renderer?
* Is the component about to be rendered?
* Has the component been rendered?
* Has the component's data been updated?
* Is the DOM about to be updated?
* Has the DOM been updated?
* Is the component about to be removed from the UI by the renderer?
* Has the component been removed from the UI by the renderer?

Both Vue and React then provide ways to hook code into those lifecycle stages:
* [Vue's API](https://vuejs.org/v2/api/#Options-Lifecycle-Hooks)
and a [nice diagram](https://vuejs.org/v2/guide/instance.html#Lifecycle-Diagram) that complements the above.
* [React's guide](https://reactjs.org/docs/state-and-lifecycle.html) and [API](https://reactjs.org/docs/react-component.html)


## Properties and State

Properties (props) and state are how UI frameworks often organise data that a component relies on.

Props are values given to a component from where the component is called for.
For example, let's pretend the `<a .../>` HTML element is a component in our UI.
In `<a href="https://developer.mozilla.org/en-US/" />`, `href` would be a prop.

_In reality, `href` is an attribute here, but that's got nothing to do with components!_

State refers to the internal data of either a component __or__ application - think of it like the memory of
a component.

State is often deeply related to the lifecycle of components, as __updating state triggers rerendering__.

However, state can be held externally in a special store, which is what things like Redux and Vuex are.
These libraries create stores that hold state, detect state changes, and trigger a top-level rerender of
your application from the top-level component all the way down to wherever the state is needed.


## VDOM

Todo.

## Diffing and Patching

Todo.
