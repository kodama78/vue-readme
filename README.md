# vue-readme
### Notes on Vue.js 
#### Initializing Vue
* `new Vue({ el: '#app' })`
    * connects an html to element to Vue
* **directives**
    * similar to angular 1
    * `v-on:input="changeTitle""` - example runs a function called changeTitle 
        * this is added to the `methods` object in the Vue object
* The **data** property in the Vue object acts very similar to **state** from react
    * Don't need to type `this.state.data`, just `data`
* The **methods** property is similar, no `this`, just write the executed function
* With `methods` and `data`, Vue allows you to access the internal parameters using the `this` keyword
* cannot use curly braces in html elements like you do w/ React.
    * you can only use curly braces where you would find text/strings
    * `<a href={ link }>` will work in React
        * WON'T WORK IN VUE
#### **directives again**
* `v-bind` bind the attribute to something in Vue
    * `v-bind:href="link"` - this will now connect to the `link` property in the Vue data object
* `v-once` - directive used to stop re-rendering
* `v-html` - tells html to render html inside of your html
* a **directive** is an instruction you place in your code
    * Vue comes w/ built in directives
    * You can create your own directives
* jsfiddle Vue exercise - https://jsfiddle.net/1saowe0r/1/
* `v-on` is used to bind any events in javascript
    * can't use `:` shortcut it seems
    * think `click`, `mousemove` those kinds of things
* `$event` - the `$` is how Vue protects certain naming conventions, like `event`
* js fiddle exercise - https://jsfiddle.net/4ujoqc32/1/
* can use **event modifiers** to events
    *`v-on:mousemove.stop=""` is an example of a built in Vue method that will stop the event
    *`v-on:mousemove.event=""` will do the stop as the `event.preventDefault()`
    *`v-on:keyup.enter.space="alertMe"` modifier to only activate the function on a certain key, in this case enter and space.
* js fiddle exercise - https://jsfiddle.net/78ntypox/5/

#### Two way data-binding
* Vue allows for two way databinding
    * uses `v-model` to tell Vue to setup 2-way data-binding on the element that it is attached to
* js fiddle exercise - https://jsfiddle.net/e5y7twh3/1/
* simplifies the communication between the model and view
    * no more `v-bind`, `v-on`, just use the `v-model`
    
#### Computed
* can look like a function, treated like a property
* can't do any logic in the data prop
* In the jsfiddle: https://jsfiddle.net/46Lr2ax3/5/
    * The difference between getting the string from `result()` and `output` is that using it in `computed` means it 
    will not continually be called like `result()` will.
    * Increase Second button will not trigger it to run since it knows that it has nothing connected to that property
    * with the console logs, you'll see that output runs only when the counter is updated, but doesn't run when secondCounter is increased
        * you'll also see that `result()` runs no matter what

#### Watched Object
* another property on the Vue object
* executes code upon data changes
* the `key` must match one of the data properties
* will need to save the vue instance if using a closure `var vm = this`
* it watches the `key`, and runs the function whenever that key changes
* js fiddle - https://jsfiddle.net/46Lr2ax3/6/

#### Dynamic CSS
* `:class` - is a Vue.js method that will combine whatever javascript is in here w/ the class you've already created
*js fiddle - https://jsfiddle.net/uq5oy9ak/1/
* js fiddle - https://jsfiddle.net/g1Lysrcp/1/

#### Conditionals
* `v-if`, `v-else` used for simple conditionals in the html
* `v-else-if` is usable in 2.1 or above
* use `<template>` to group DOM elements for non-nested `v-if`'s
* `v-show` does not remove the element from the DOM like `v-if` does. Gives it a `display: none`
* jsfiddle - https://jsfiddle.net/u0w7ptd4/1/

#### Lists
* use a `for in` syntax. Put the property that you want in the `li`
* for multiple items off an array/object, use parentheses
    * order matters
    * the first item will always be the value from the item in the array/object
    * the second will always be the index
* use a `template` for using multiple HTML elements in a single loop
* you can also loop through objects, like using a normal `for in` loop in JS
    * you can use `()` again to access the `value` and the `key` in the objects
        * order matters
        * first is the value
        * second is the key
        * third is the index
* you can loop through numbers
    * `n in 10` works
* `push` method
    * Vue actually proxies the `push` method OG method
    * to be safe, you need to assign a key w `v-bind` or `:key` to make sure that Vue keeps track of the list item
        * just like react 
* js fiddle - https://jsfiddle.net/xy5zg3jk/4/ 
