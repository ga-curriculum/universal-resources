# Build a Browser Game Walkthrough

This is a walkthrough of the steps you should take to start your browser game project. This walkthrough is meant to be used only when your project planning is over, and you are ready to start coding. If you still need to plan your project, please go back to the [Planning your Browser Game](./planning-your-browser-game.md) and follow the steps there.

## Overview

It's suggested that you read through all instructions and then follow the checklist at the end to ensure you have completed all steps in order.

### Step 1: Create a remote repository

Create a remote repository in your **PERSONAL** GitHub account. You will not need to initialize the repository with a README or a `.gitignore` file. When considering the name for your game's repository, using a name representing your choice of game, e.g., "tic-tac-toe", is better than something like "project-1".

### Step 2: Clone down the repository

Using the `Quick Setup` option, clone your newly created repository into your `~/code/ga/projects` directory.

> If your project uses an API, create a `.gitignore` file and add your `.env` file. You can do this by running `touch .gitignore` and adding `.env` to the file. This will ensure that your API key is not pushed to GitHub.

### Step 3: Create project files

Navigate into your freshly cloned repository and create the following folders and files:

- **index.html**
- **css/style.css**
- **js/app.js**

### Step 4: Add boilerplate HTML

Create the HTML boilerplate within **index.html** using `![tab]`. Add a `<title>` tag with the name of your game. Add a `<link>` tag to the **css/style.css** file. Add a `<script>` tag to the **js/app.js** file.

> Add `defer` to the `<script>` tag. This will ensure the JavaScript file is loaded after the HTML and CSS files.

### Step 5: Add a README.md file

Create a README.md file in your project directory using `touch README.md`. Add a title to the README.md file using `#` and the name of your game.

Before the end of the project, you will need to update the `README.md` with any and all project requirements.

### Step 8: Organize the app's JS into sections
    
It's nice to keep similar code in the same place. This makes it easy to find what you're looking for. It might be helpful to have comments marking the various sections of your code like so:

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

- [ ] Created a remote repository in your **PERSONAL** GitHub account.
- [ ] Cloned down the repository to your `~/code/ga/projects` directory.
- [ ] Created project files.
- [ ] Added the HTML boilerplate to **index.html**.
- [ ] Add README.md file.
- [ ] Organized the app's JS into sections.

### Get Started Coding

You've just completed the above steps for setting up your project. Now, you're ready to start coding. Here is a suggested order of steps to take to get started coding:

1. Start with some HTML in `index.html` for the basic layout of the UI. You can reference the JavaScript Browser Game - Rock, Paper, Scissors lesson for an example of how to do this.

> If an element's content comes from a `render()` function, you may want to temporarily include mock content in the HTML to help with layout and styling. However, once the content is provided by the `render()` function, you should remove the mock content from `index.html`.

2. Declare, but don't initialize the application-wide state variables. The initialization of the variables to their **"initial"** state should be done within an `initialize()`, or similarly named function, e.g., `init()`.

3. Write that `initialize()` function.

4. Invoke `initialize()` to "kick-off" the app.

5. Now that the `initialize()` function has initialized the state variables, the last line in `initialize()` should be `render();` to render that state to the DOM for the first time.

6. Declare that `render()` function.

7. As a reminder, after the state has been updated in an event listener, the last line of code in the event listener function should be a call to `render();` again, to render the state to the DOM. Here's an example:
        
```javascript
const handleMove = (event) => {

    //Logic for the event handler, update state variables, etc

    //Render data to the DOM
    render();
}
```

8. Register event listeners

9. Code the event listener(s)

### Changing user stories to Pseudocode

While coding, you may notice that you have strayed from your original plan. As you are coding, you may need to add or remove something. Or you might have run into a bug you did not plan for. This is normal! The goal here is to work through the unexpected without being stopped.

Always refer back to the project requirements and your user stories. It's okay to change the plan as you go; it's typical and expected. Just ensure you are still meeting the project requirements and your user stories are still accurate.

### Commit Often

While working on your project, you should be committing often. You should be committing after every significant change you make. This will help you keep track of your progress and will help you if you need to revert to a previous version of your code.

Refer to your project documentation for more details on commit requirements.

### Data-Centric Approach

**Data is the single source of truth of any application.**

When building a browser game, there will no doubt be data that needs to be tracked/remembered. This data is often referred to as the application's **state**.

Regarding "making the app work", DOM manipulation is secondary to data manipulation.

When coding event listener functions, ask yourself,

> "What state (data) needs to be updated and how?"

instead of thinking about what to change in the DOM.

When coding the `render()` function(s), you'll get to think about the DOM.

Following a "data-centric" approach, developers can test the application's logic more easily. In fact, we can test out much of the app in the console (assuming you keep your functions and state in global scope while developing the app)! For example, you can type something like `getWinner()` in the console to check what value is being returned from that function. 

An easy mistake new programmers make is using the **DOM** to hold state/information. Instead, we need to use variables to hold **all** data that needs to be tracked during runtime, i.e., when a program is running.

By following this approach, a developer can re-use much of an application's code if the application needs to be ported to other platforms such as mobile and desktop.

### Data Best Practices: Use Constants for Non-Changing Information

**Use constants instead of literal values to improve code readability and maintenance.**

For example, let's say you wanted to *limit the amount of guesses* in a game to a specific number.

You could write code like this:

```js
let lose = numGuesses > 5;
```

However, the following code might be preferable,

```js
const MAX_GUESSES = 5;
let lose = numGuesses > MAX_GUESSES;
```

For the following reasons:

- Using a constant variable and good naming conventions would make understanding the logic easier.
- This code is also more maintainable because you will probably need to use the maximum guess value in more than one code section.

> Why is `MAX_GUESSES` in all caps? This is a standard convention for constants. It's a way to visually distinguish constants from other variables.

### Data Best Practices: Use Objects and Arrays to Hold Related Data

**Instead of using several separate variables to store data, consider using objects and arrays to hold related data.**

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

This avoids the risk of data becoming out of sync or inconsistent. The following code:

```javascript
let numHats = 5;
let numCoats = 10;
let numHatsCoats = 15;

if (numHatsCoats > 20) {
    console.log("That's a lot of clothing");
};
```

Could be rewritten as:

```javascript
let numHats = 5;
let numCoats = 10;

if (numHats + numCoats > 20) {
    console.log("That's a lot of clothing");
};
```

In the first example, every time either `numHats` or `numCoats` changes, you must update `numHatsCoats` to ensure the `if` statement works as expected. This is error-prone. If you simply compute values, it's much safer.

### Data Best Practices: Cache DOM Elements

Suppose the code needs to access a DOM element (or elements) more than once during runtime. In that case, selecting and caching that element/those elements in a variable is generally a good idea. DOM elements are like any hard-coded value. If you can store them somewhere, it's generally a good idea. Also, the browser doesn't have to look through the DOM multiple times to find the same element(s). You won't see a difference in speed for most applications, but with a very large app, you might.

### Data Best Practices: Update the DOM Via `render()` Functions

**The `render()` function's responsibility is to visually represent all state in the DOM**.

This includes the hiding/showing parts of the UI based on the application's state.

For example, a `render()` function could handle under what circumstances and how the following are displayed on the page:

- the player's name
- player score
- a message like "Your turn" during a player's turn
- "Game Over/Winner"
- info about the other player

You should avoid updating the DOM outside the `render()` function(s). However, there are exceptions to this rule, such as "eye candy" animations, a ticking time display, etc.

### Data Best Practices: Use Several `render___()` Functions

**Use multiple render-related functions dedicated to a specific rendering task.**

The main `render()` function can grow quite large. If you find this happening, break that function into additional `render()` functions that each take care of a specific aspect of the app's state.

For example:

```js
const render = () => {
    renderBoard();
    renderScores();
    renderControls();
    renderMessages();
}
```
