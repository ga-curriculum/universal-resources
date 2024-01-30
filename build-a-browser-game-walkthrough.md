# Build a Browser Game Walkthrough

This is a walkthrough of the steps you should take in order to start your browser game project. This walkthrough is meant to be used only when your project planning is over and you are ready to start coding. If you have not yet planned your project, please go back to the [How to Build a Browser Game Guide](./how-to-build-a-browser-game-guide.md) and follow the steps there.

## Overview

It's suggested that you first read through all instructions then follow the checklist at the end to make sure you have completed all steps in order.

### Step 1: Create a new project directory

Create a directory for the project in the `~/code/ga/projects` folder.  When thinking about the name for your game's directory, using a name that represents your choice of game, e.g., "tic-tac-toe", is better than something like "project-1".

### Step 2: Create project files

Create the following folders and files in your project directory:

- **index.html**
- **css/style.css**
- **js/app.js**

### Step 3: Add boilerplate HTML

Create the HTML boilerplate within **index.html** using `![tab]`. Add a `<title>` tag with the name of your game.  Add a `<link>` tag to the **css/style.css** file.  Add a `<script>` tag to the **js/app.js** file.

> Be sure to add `defer` to the `<script>` tag. This will ensure that the JavaScript file is loaded after the HTML and CSS files.

### Step 4: Create a local git repository

Initialize a local git repository in your project directory using `git init`. Add and commit your files.

> If your project is going to be using an API, create a `.gitignore` file and add your `.env` file to it. You can do this by running `touch .gitignore` and then adding `.env` to the file.  This will ensure that your API key is not pushed to GitHub.

### Step 5: Create a remote repository

Create your remote repository in your **PERSONAL** GitHub account - be sure **NOT** to check the "Initialize this repository with a README" checkbox (you'll want to `touch README.md` locally).

### Step 6: Add remote repository to local repository

Run the terminal command that the GitHub instructions provide to add the remote in your local repo.  It will look like this:

```bash
git remote add origin <the URL to your repo>
```

Push your local repo to the remote repo using `git push origin main`.

> If you get an error, check which branch you are on using `git branch`.  If you are on `master`, you will need to run `git push origin master` instead. You can also update your default branch to `main` by running `git branch -M main`.

### Step 7: Add a README.md file

Create a README.md file in your project directory using `touch README.md`. Add a title to the README.md file using `#` and the name of your game.

Before the end of the project, you will need to update the `README.md` with any and all project requirements.

### Step 8: Organize the app's JS into sections
	
In general, it's nice to keep similar code in the same place. This makes it easy to find what you're looking for. It might be helpful to have comments marking the various sections of your code like so:

```js
/*-------------- Constants -------------*/


/*---------- Variables (state) ---------*/


/*----- Cached Element References  -----*/


/*-------------- Functions -------------*/


/*----------- Event Listeners ----------*/

```

### Step 9: Code Away!

Now that you have your project set up, you can start coding!

## Get Started Checklist

- [ ] Created a new project directory
- [ ] Created project files
- [ ] Added boilerplate HTML
- [ ] Created a local git repository
- [ ] Created a remote repository
- [ ] Added remote repository to local repository
- [ ] Added a README.md file
- [ ] Organized the app's JS into sections
- [ ] Coded away!

## As you Code Reference

As you are working on your project, you may need to reference the following lessons:

- Intro to the DOM
- DOM Events
- JavaScript Browser Game - Rock, Paper, Scissors
- JavaScript Browser Game - Tic Tac Toe Lab
- Intermediate CSS
- Flexbox

### Get Started Coding

You've just completed the above steps for setting up your project. Now you're ready to start coding. Here is a suggested order of steps to take to get started coding:

1. Start with some HTML in `index.html` for the basic layout of the UI. You can reference the JavaScript Browser Game - Rock, Paper, Scissors lesson for an example of how to do this.

> If an element's content is going to come from a `render()` function, you may want to temporarily include mock content in the HTML to help with layout and styling. However, once the content is being provided by the `render()` function, you should remove the mock content from `index.html`.

2. Declare, but don't initialize, the application-wide state variables. The initialization of the variables to their **"initial"** state should be done within an `initialize()`, or similarly named function, e.g., `init()`.

3. Write that `initialize()` function.

4. Invoke `initialize()` to "kick off" the app.

5. Now that the `initialize()` function has initialized the state variables, the last line in `initialize()` should be `render();` to render that state to the DOM for the first time.

6. Declare that `render()` function.

7. As a reminder, after state has been updated in an event listener, the last line of code in the event listener function should be a call to `render();` again, to render the state to the DOM.  Here's an example:
		
```javascript
const handleMove = (event) => {

    //Logic for the event handler, update state variables, etc

    //Render data to the DOM
    render();
}
```

8. Register event listeners

9. Code the event listener(s)

### User Stories and Psuedocode

While you are coding, you may notice that you have strayed from your original plan. As you are coding, you may find that you need to add or remove something. Or you might have run into a bug that you did not plan for. This is normal! The goal here is to work through the unexpected and not be stopped by it.

Always refer back to the project requirements and your user stories. It's okay to make changes to the plan as you go, in fact it's normal and expected. Just make sure that you are still meeting the project requirements and that your user stories are still accurate.

### Commit Often

While working on your project, you should be committing often. You should be committing after every major change you make. This will help you keep track of your progress and will help you if you need to revert back to a previous version of your code.

Refer to your project documentation for more details on commit requirements.

### Data-Centric Approach

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

### Data Best Practices: Use Constants for Non-Changing Information

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

> Why is `MAX_GUESSES` in all caps?  This is a common convention for constants. It's a way to visually distinguish constants from other variables.

### Data Best Practices: Use Objects and Arrays to Hold Related Data

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

### Data Best Practices: Don't Store State That Can be Computed

Try not to store any state data that can be computed from other data.

This avoids the risk of data becoming out of sync or inconsistent.  The following code:

```javascript
let numHats = 5;
let numCoats = 10;
let numHatsCoats = 15;

if (numHatsCoats > 20) {
	console.log("That's a lot of clothing");
};
```

could be rewritten as:

```javascript
let numHats = 5;
let numCoats = 10;

if (numHats + numCoats > 20) {
	console.log("That's a lot of clothing");
};
```

In the first example, every time either `numHats` or `numCoats` changes, you would have to update `numHatsCoats` in order to make sure the `if` statement works as expected. This is error prone. If you simply compute values, it's much safer.

### Data Best Practices: Cache DOM Elements

If the code needs to access a DOM element (or elements) more than once during runtime, it's generally a good idea to select and cache that element/those elements in a variable. DOM elements are like any hard coded value. If you can store them somewhere, it's generally a good idea. Also, this way the browser doesn't have to look through the DOM to find the same element(s) multiple times. For most applications, you won't see a difference in speed, but with a very large app, you might.

### Data Best Practices: Update the DOM Via `render()` Functions

**The `render()` function's responsibility is to visually represent all state in the DOM**.

This includes the hiding/showing of parts of the UI based upon the application's state.

For example, a `render()` function could handle under what circumstances and how the following are displayed on the page:

- the player's name
- player score
- a message like "Your turn" during a player's turn
- "Game Over/Winner"
- info about the other player

You should avoid updating the DOM outside of the `render()` function(s). There are exceptions to this rule, however, such as "eye candy" animations, a ticking time display, etc.

### Data Best Practices: Use Several `render___()` Functions

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
