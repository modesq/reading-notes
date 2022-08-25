# reading-notes

## CLASS 01

------

## CLASS 02

------

## CLASS 03

------

## CLASS 04

1. What is a ‘Controlled Component’?

    a component that is conrtolled by react, it takes its current calue via props and notifies changes via callback functions.
2. Should we wait to store the users responses from the form into state when they submit the form OR should we update the state with their responses as soon as they enter them? Why.
    we should wait until the user submits the form, then we should store the responses in the state. this will prevent errors from the users and allow them to change and revies the entered responses before they get stored.

3. How do we target what the user is entering if we have an event handler on an input field?

    we log the text content of the input field by storing them from the fields where the event handler called the storing functions using the following code as an example:
            `log.textContent = e.target.value;`

------

## CLASS 05

### part 1

1. What is the single responsibility principle and how does it apply to components?

    this principle states that every function, class and module is responsible for exactly one resposnibility, and that includes components too.
2. What does it mean to build a ‘static’ version of your application?

    a web page that doesnt change, its wrtitten in with fixed HTML code and stored in a web server exactly as viewed by the user.
3. Once you have a static application, what do you need to add?

    interactivty that can will be bulit using states and inverse data flow using fuctions.
4. What are the three questions you
can ask to determine if something is state?

    1. Is it passed in from a parent via props? If so, it probably isn’t state.
    2. Does it remain unchanged over time? If so, it probably isn’t state.
    3. Can you compute it based on any other state or props in your component? If so, it isn’t state.

5. How can you identify where state needs to live?

    by figuring out the absolute minimal representation of the state your application needs and compute everything else you need on-demand.

### part 3

1. What is a “higher-order function”?

    it is a function that takes fucntions as arguments or returns a fucntion.
    all other functions are called first-order functions.

2. Explore the greaterThan function as defined in the reading. In your own words, what is line 2 of this function doing?

    it is basically a function that takes one argument (n) and returns another function with its own argument (m) that compares these two, to return a boolean value depending on the result of that comparison.

3. Explain how either map or reduce operates, with regards to higher-order functions.

    map basically works by using a fucntion that is passed to another fucntion which itterates through the array passed to the fucntion, all of that will return a new array containing the same number of elements as the original array, yet it may have different elements depending on the fucntion being passed to that itterative function.
