# Lesson Setup

A guide to setting up your development environment for lessons.

Before you begin any lesson, it's essential to have your development environment ready. We'll provide you with two flexible methods for executing your javascript code. 

## Create Your Files

1. Open your Terminal application and navigate to your `~/code/sei/lectures` directory:

```bash
cd ~/code/ga/lectures
```

2. Create and enter a new folder for the current lesson:

```bash
mkdir lesson-name
cd lesson-name
```

3. Create any necessary files for the lesson.

```bash
touch app.js index.html style.css
```

You likely wont need all of these for every lesson. You're instructor can provide guidance on the files needed for each lesson. 


4. Open the directory in VS Code.

```bash
code .
```

## Method 1: Browser Console


1. Open `index.html` and insert HTML boilerplate. Add the following line within the `<head>` tag to link your `app.js` file:
    ```html
    <script defer src="./app.js"></script>
    ```

2. Open `index.html` in your web browser. :rocket:

*There are several popular options for opening code in the browser using VS Code extensions. Download one of the following extensions:*

 - [open in browser](https://marketplace.visualstudio.com/items?itemName=techer.open-in-browser)
   -  Following installation, files in the vscode can be opened in the browser by right clicking and selecting `Open in Default Browser`
 - [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)
   - Following installation, files can be opened by clicking `Go Live` in the bottom right corner of the status bar in vscode.
 - [Live Preview](https://marketplace.visualstudio.com/items?itemName=ms-vscode.live-server)
   - Following installation, preview your HTML files quickly by clicking the double pane `Show Preview` button in the top right corner of the file. 


3. If running `Javascript` only, access the console output via your browser's Developer Tools.


## Method 2: Node.js

- Run the `app.js` file directly from your terminal using Node.js:
```bash
node app.js
```

**Note**: Both methods are effective, but it's recommended to use the same method as your instructor for a smoother learning experience.