# ![[How to Build a Browser Game Guide]](./assets/hero.png)

**Learning objective:** By the end of this lesson, students will be able to create a browser application with the necessary structure and reopsitories.

## Introduction

Getting started and knowing how to structure the code in an application is one of the most difficult things for students to figure out.

You will not just learn about how to use languages, libraries and frameworks in this course. An important aspect of programming you will also be learning about is how to structure code and apply logic while implementing the features of a web application.

## Process

The following diagram conceptually shows us how we could go about coding a browser-based game (***actually, pretty much any browser-based app such as a calculator, a to-do app, etc.***):

![Browser Game App Flow](./assets/browser-game-app-flow.png)

## Steps to Getting Started on a Browser Game

The following approach has been proven to help students write complex front-end web apps, not just games.

1. **Analyze the app's functionality**
	
	The app's features, from the user's point of view, should be described using *User Stories*.
	
	Ideally a user story follows this template:
	
	**As a [role], I want [feature] because [reason]**.
	
	Example user story: *As a player, I want to see a list of high-scores so that I know what score I will need to make the list.*
	
	This doesn't have to be exact, but the point is to think carefully about what the user will be able to do, not necessarily how you will build it.
	
2. **Think about the overall design (look & feel) of the app**
	
	This is less about making something beautiful than it is about how to lay out the elements in your app so that it's responsive.  What will it look like in Mobile?  Tablet?  Desktop?
	
3. **Wireframe the UI**
	
	Wireframes provide a blueprint for the HTML & CSS.  Wireframes also help reveal an application's state and functionality.  They kind of look like this:
	
	![](https://balsamiq.com/assets/learn/articles/mobile-web.png)
	
4. **Pseudocode**
	
	Pseudocode outlines the app's logic using plain language. It provides a road map to writing the code itself.
	
	For example, pseudocoding:
	
	- the logic for when a player makes a move
	- checking if the game has been won
	- etc.
	- ...
	
	will prove to be helpful when writing the actual code.  Pretend that you're writing instructions on how to write the app to a programmer who will do the actual coding.  You want to give them a high level overview of what they will do, without getting too deep into the code itself.  Here's an example:
	
	1. Initialize a variable that will hold the number of times a button has been pressed.  Initially it's 0.
	1. Set up a click handler for the button on the page
	1. When the user clicks the button, increment the variable that contains how many times the button was clicked.
	1. Once the value is incrememnted, update the place in the DOM that contains that value
	
5. **Identify the application's state (data)**
	
	What does the application need to "remember" throughout its execution?  Most of the time these variables will change, as the user interacts with the app.  In the previous example for pseudo code, it needed to remember how many times the button was pressed.
	
	Use the wireframe and pseudocode to help identify what state needs to be tracked.
	
6. **Set up the project**
	
	Create a directory for the project in the `~/code/ga/projects` folder.  When thinking about the name for your game's directory, using a name that represents your choice of game, e.g., "tic-tac-toe", is better than something like "project-1".  
	
	- Create the starting directories and files within the project folder:
		
		- **index.html**
		- **css/style.css**
		- **js/app.js**
		
	- Create the HTML boilerplate within **index.html** using `![tab]`.
	
	- Link **style.css** in the `<head>`.
	
	- Add a `<script>` tag to load the **app.js** in the `<head>`.
	
		Be sure to use the `defer` attribute to ensure that the DOM is ready before the script runs.
	 
		```html
		<script defer src="js/app.js"></script>
		```
	
7. **Create a local repo**
	
	- Make your project a local repo with `git init`.
	
	- Hopefully when you created the directory for your game you used a name that represents your choice of game, e.g., "tic-tac-toe", rather than something like "project-1". It's also recommended that the name of the remote repo on GitHub and the project directory of your local repo match.
	
	- Create your remote repo in your **PERSONAL** GitHub account - be sure **NOT** to check the "Initialize this repository with a README" checkbox (you'll want to `touch README.md` locally).
	  
	- Run the terminal command that the GitHub instructions provide to add the remote in your local repo.  It will look like this:
	
		```
		git remote add origin <the URL to your repo>
		```
	  
	- Make your first commit:  `git add -A`, then `git commit -m "Initial commit"`
	  
	- Push the commit to the repo for the **first time** using: `git push -u origin main`.  
	
	- Future pushes can now be made using just `git push`.
	
8. **Organize the app's JS into sections**
	
	In general, it's nice to keep similar code in the same place.  This makes it easy to find what you're looking for.  It might be helpful to have comments marking the various sections of your code like so:
	
	```js
	/*-------------- Constants -------------*/
	
	
	/*---------- Variables (state) ---------*/
	
	
	/*----- Cached Element References  -----*/
	
	
	/*-------------- Functions -------------*/
	
	
	/*----------- Event Listeners ----------*/
	
	```
	
9. **Code away!**
	
	- It might be helpful to start with some HTML in `index.html` for the basic layout of the UI. If an element's content is going to come from a `render()` function, you may want to temporarily include mock content in the HTML to help with layout and styling. However, once the content is being provided by the `render()` function, you should remove the mock content from `index.html`.
	- Declare, but don't initialize, the application-wide state variables. The initialization of the variables to their **"initial"** state should be done within an `initialize()`, or similarly named function, e.g., `init()`.
	- Write that `initialize()` function.
	- Invoke `initialize()` to "kick off" the app.
	- Now that the `initialize()` function has initialized the state variables, the last line in `initialize()` should be `render();` to render that state to the DOM for the first time.
	- Declare that `render()` function.
	- As a reminder, after state has been updated in an event listener, the last line of code in the event listener function should be a call to `render();` again, to render the state to the DOM.  Here's an example:
		
		```javascript
		const handleMove = (event) => {

			//Logic for the event handler, update state variables, etc

			//Render data to the DOM
			render();
		}
		```
	- Register event listeners
	- Code the event listener(s)
	
11. **Make frequent git commits**
	
	At a minimum, commit after each "milestone" or feature implementation.
	
## Data-Centric Approach

**Data is the single source of truth of any application.**

When building a browser game, there will no doubt be data that needs to be tracked/remembered. This data is often referred to as the application's **state**.

When it comes to "making the app work", the manipulation of the DOM is secondary to data manipulation.

When coding event listener functions, ask yourself,

> "What state (data) needs to be updated and how?"

instead of thinking about what to change in the DOM.

You'll get to think about the DOM when coding the `render()` function(s).

By following a "data-centric" approach, developers can more easily test the application's logic - in fact, we can test out much of the app in the console (assuming you keep your functions and state in global scope while developing the app)! For example, you can type something like `getWinner()` in the console to check what value is being returned from that function. 

An easy mistake new programmers make is using the **DOM** to hold state/information.  Instead, we need to use variables to hold **all** data that needs to be tracked during runtime, i.e., when a program is running.

By following this approach, a developer can re-use much of an application's code  if the application needs to be ported to other platforms such as mobile and desktop.

## Data Best Practices:

### Use Constants for Non-Changing Information

**Use constants instead of literal values to improve code readability and maintenance.**

For example, let's say you wanted to *limit the amount of guesses* in a game to a specific number.

You could write code like this:

```js
let lose = numGuesses > 5;
```

However, the following code might be preferable,

```js
let lose = numGuesses > MAX_GUESSES;
```

for the following reasons:

- Using a constant variable and good naming conventions would make it easier to understand what the logic is.
- This code is also more maintainable because you will probably need to use the maximum guesses value in more than one section of code.

### Use Objects and Arrays to Hold Related Data

**Instead of using several separate variables to store data, consider using objects and arrays to hold related-data.**

For example, if you need to track info for two players, instead of using several variables like `player1name`, `player2name`, `player1score`, `player2score`, etc., use an array of objects instead:

```js
const players = [
	{
		name: '',
		score: 0
	},
	{
		name: '',
		score: 0
	}
];
```
	
Following this practice will result in **much more concise code** and make it easier to implement certain features.

### Don't Store State That Can be Computed

Try not to store any state data that can be computed from other data.

This avoids the risk of data becoming out of sync or inconsistent.  The following code:

```javascript
let numHats = 5;
let numCoats = 10;
let numHatsCoats = 15

if(numHatsCoats > 20){
	console.log("That's a lot of clothing");
}
```

could be rewritten as:

```javascript
let numHats = 5;
let numCoats = 10;

if(numHats + numCoats > 20){
	console.log("That's a lot of clothing");
}
```

In the first example, every time either `numHats` or `numCoats` changes, you would have to update `numHatsCoats` in order to make sure the `if` statement works as expected.  This is error prone.  If you simply compute values, it's much safer.

### Cache DOM Elements

If the code needs to access a DOM element (or elements) more than once during runtime, it's generally a good idea to select and cache that element/those elements in a variable.  DOM elements are like any hard coded value.  If you can store them somewhere, it's generally a good idea.  Also, this way the browser doesn't have to look through the DOM to find the same element(s) multiple times.  For most applications, you won't see a difference in speed, but with a very large app, you might.

### Update the DOM Via `render()` Functions

**The `render()` function's responsibility is to visually represent all state in the DOM**.

This includes the hiding/showing of parts of the UI based upon the application's state.

For example, a `render()` function could handle under what circumstances and how the following are displayed on the page:

- the player's name
- player score
- a message like "Your turn" during a player's turn
- "Game Over/Winner"
- info about the other player

### Use Several `render___()` Functions

**Use multiple render-related functions dedicated to a specific rendering task.**

The main `render()` function can grow quite large.  If you find this happening, break that function apart into additional `render()` functions that each take care of a specific aspect of the app's state.

For example:

```js
const render = () => {
	renderBoard();
	renderScores();
	renderControls();
	renderMessages();
}
```

### Avoid Updating the DOM Outside of `render()`

Note: There are exceptions to this rule, however, such as "eye candy" animations, a ticking time display, etc.