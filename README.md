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
