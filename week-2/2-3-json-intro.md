# 2.3: Intro to JSON challenges

After taking a quick look at one less-than-ideal option for persistent data in [the previous section](https://github.com/LearnTeachCode/intro-javascript-class/blob/may-2018-int/week-2/2-2-persistent-data.md), we've come to the conclusion that there's only one convenient way to share data in a web app across multiple computers: *send it over the internet!* This brings us to a topic important for both databases and APIs: JavaScript Object Notation, also known as **JSON**!

<hr/>

## Challenge 1:

So, we know that in order to create a multiplayer click-counting game, one way or another we'll need to send the player's information over the internet. Let's approach this challenge by starting with a silly activity!

First, make sure you've played the game from the previous section and keep it open in a tab for quick reference: https://dragon-defeater-v1-localstorage.glitch.me/

Next -- and yes, this is silly, but bear with me! -- **write me an email to send me the data from your game.** Take the information that you saved in *your specific game*, and type it or copy-paste it or somehow get it into the body of an email, and then send it to me! There's no correct answer here, as long as you communicate the data in a way I can read and understand!

**Discuss:**

  1. Taking a look at what you typed into your email, is that code? Why or why not?
  2. What if you had to send me the data from a JavaScript object that had *hundreds* of key-value pairs? How would you do that?

<br/>

## Data formats are like ice cream flavors: so many to choose from!

As we saw, there are many different ways to format and communicate the same exact data (the same information). That brings us to an important distinction:

:star: There's a big difference between ***the data itself***, stored in the computer's memory, and the many possible ***representations*** of that data once it's transformed into a human-readable string of characters.

For example, here's how some sample data for our game could be represented with JavaScript's object literal notation:

```javascript
let currentUser = {
	name: "Liz",
	email: "liz@example.com",
	dragonsDefeated: 17
};
```

Here's how the same data looks if formatted in **CSV**, [Comma-Separated Values](https://en.wikipedia.org/wiki/Comma-separated_values), which is a standard file format used for spreadsheets:

```csv
name, email, dragonsDefeated
"Liz", "liz@example.com", 17
```

And here's the same data formatted in **XML**, [Extensible Markup Language](https://en.wikipedia.org/wiki/XML) (basically a more flexible version of the HTML we use to structure the content of web pages):

```xml
<currentUser>
  <name>Liz</name>
  <email>liz@example.com</email>
  <dragonsDefeated>17</dragonsDefeated>
</currentUser>
```

:star: **The point is: information can't be communicated without also being formatted. (And you need to use a format that others can recognize and understand!)**

It's just like how we communicate with other humans: first we need to convert (or ***format***) the thoughts in our brains (*the raw data*) into *actual words*. (And only people who speak the same language as you can understand what you say!)

<br/>

## Challenge 2:

As we've seen, the programmers who created our web browsers included a very convenient feature for interactively viewing JavaScript objects whenever you `console.log()` them. Thank goodness!

**But try this:** open a new tab in your browser, then open the JavaScript console while you're on that tab, and copy-paste the example code below:

```javascript
let exampleObject = {
	exampleProperty: "some data here",
	exampleKey: "some data goes here too"	
};

// This worked before to display strings on the page, so we should
// expect it to work with displaying entire objects too, right?
document.body.textContent = exampleObject;
```

**Discuss:**

  1. What happened?
  2. Why did it behave that way?
  3. How could we take that object's data and display it on the web page? (In other words, how can we solve this challenge of *communicating* or *transferring* the data from the computer's memory to the user's eyes?)

<br/>

## So what is JSON exactly?

This is going to feel a bit anticlimactic: **JSON** (**JavaScript Object Notation**) is just another data format that's almost an exact copy of JavaScript's *object literal* notation.
  
***So if you know how to create a JavaScript object like we've been doing so far, you already understand JSON!***

Here's what the example object from the previous challenge looks like as a string in the JSON data format:

```
{"exampleProperty":"some data here","exampleKey":"some data goes here too"}
```

You can also display strings of JSON formated data with the indentations we've been using in our code -- just like in JavaScript, spaces in between different values don't matter for JSON:

```
{
  "exampleProperty": "some data here",
  "exampleKey": "some data goes here too"	
}
```

**JavaScript has a couple of built-in functions for working in JSON, and one of them is `JSON.stringify()`**. It takes a JavaScript object as input and converts it into exactly what we need for our previous challenge: one giant string containing the data in JSON format.

Let's try it out!

<br/>

## Challenge 3:

In [Python Tutor](http://pythontutor.com/javascript.html#mode=edit), fill in the blanks in the following code snippet to turn the object into a JSON-formatted string and display it in the console:

```javascript
let currentUser = {
	name: "Liz",
	email: "liz@example.com",
	dragonsDefeated: 17
};

// *** Fix the line of code below:
// You need to use the object from above as the input to JSON.stringify()
let jsonFormattedString = JSON.stringify();

// *** Then display the value of jsonFormattedString in the console!
// Your code here:

```

The console should display a string of characters in the JSON data format:

```
{"name":"Liz","email":"liz@example.com","dragonsDefeated":17}
```

*And that's what JSON looks like: basically the same format as we've been using to create our JavaScript objects!*

<br/>

## And why is this JSON stuff useful?

Going back to our silly email-writing activity from before, **now we have a much better way to package up (to *format*) the data from our game so that we can send it over the internet:** just use the `JSON.stringify()` function to turn it into a giant string!

Not only does this save us a lot of typing, but now that we're using a ***standardized*** data format used by other programmers all over the world, we have an easy way to store, send, and receive information from many different software applications!

This opens up all sorts of possibilities:

  - Storing the data in many types of databases (like Firebase), to have *truly* persistent data that can be accessed across multiple devices!
  - Sharing data between different users (to make a competitive or cooperative multiplayer game)
  - Sending our data to an API (for example, to publish our score on Facebook or Twitter)

<br/>

## Bonus challenge 1:

Combine the code from challenge #2 and challenge #3 above to solve our problem in challenge #2: now you should finally be able to display the example object's data on the **web page** itself!

<br/>

## Bonus challenge 2:

What do you think the term *"machine-readable format"* means, compared to *"human-readable format?"* Search online for how other people define both of those terms, and see if you can find some examples that illustrate the difference between them.

<br/>

## Bonus challenge 3:

What's the *other* built-in JSON function? And what does it do? Why is it useful? Look around online and see what you find!

  > This is a topic we'll return to later, when we start working with third party web APIs.

<br/>

## Bonus info: Rules for the JSON data format

We'll come back to this topic in more detail later, but if you're curious, here's a quick look at a couple important rules for formatting JSON data:

  - JSON can contain strings, numbers, Booleans, objects, arrays, and the `null` data type.
  
  - But you ***cannot*** put functions inside your JSON data! (Since by definition, data doesn't really *do* anything on its own; it just sits there, waiting for some software program to do something with it.)
  
  - You also cannot use `undefined` as a value in JSON data.

  - In valid JSON, the property names (or keys) of any objects must be ***strings***, as in `{"exampleKey": "example value"}`. Experiment with using `JSON.stringify()` some more and you'll notice that slight difference.
  
  > **Note:** It's also perfectly valid in your JavaScript code to put quote marks around the keys/properties of your objects. (In fact, in some special cases you *need* to -- but that's a topic for later!)

<br/>

<hr/>

:trophy: ***Great job!*** You now know the very basics of how to package up your data in preparation to send it somewhere, whether to a database or a third-party web API (topics we'll get to soon enough)!

:point_right: **Next up:** in [section 2.4, we'll start learning about the Firebase database library with the important concept of **paths**](https://github.com/LearnTeachCode/intro-javascript-class/blob/may-2018-int/week-2/2-4-firebase-paths.md), which we need in order to access data from the databases that we'll be building later!
