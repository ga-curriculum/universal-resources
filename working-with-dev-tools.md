# Working with DevTools

Note: While most browsers offer a version of DevTools, this guide is specifically for Google Chrome's DevTools. 

## What are DevTools?

Chrome DevTools are a set of built-in debugging and inspection tools for webpages within the Google Chrome browser. They provide functionalities for examining the structure, behavior, and performance of webpages, allowing developers and users to identify and solve issues, optimize resource usage, and experiment with different configurations.

### Key features of DevTools

- **Element Inspection**: Examine the Document Object Model (DOM) structure of a webpage, including HTML elements, their attributes, and CSS styles. This allows for real-time modification of styles and visual debugging of layout issues.

tktk hunter -- ss here

- **Network Analysis**: Monitor network requests and responses made by the webpage, including details like timestamps, status codes, and transferred data. This helps identify performance bottlenecks and diagnose network-related issues.

tktk hunter -- ss here
  
- **Console Panel**: Execute JavaScript code in the browser context, allowing for testing logic, debugging scripts, and manipulating webpage elements dynamically.

tktk hunter -- ss here

- **Sources Panel**: Inspect and debug JavaScript source code files associated with the webpage, including setting breakpoints, stepping through code execution, and examining variable values.

tktk hunter -- ss here

- **Performance Panel**: Analyze the webpage's performance by recording and visualizing resource usage and execution timelines. This helps identify performance bottlenecks and optimize resource allocation.

tktk hunter -- ss here

- **Additional Tools**: Various other tools are available depending on the webpage and browser version, such as the Application panel for inspecting storage mechanisms, the Security panel for analyzing security certificates, and the Recorder panel for capturing user interactions for playback and analysis.

## Accessing DevTools

There are two ways to access DevTools:

- Right-click anywhere on a webpage: Choose "Inspect" from the menu that pops up. This opens the DevTools panel, revealing a treasure trove of information about the page.

tktk hunter -- ss here

- Keyboard shortcuts: For power users, Chrome offers quick access with keyboard shortcuts like `Ctrl+Shift+I` (Windows/Linux) or `Command+Option+I` (Mac).

## Elements panel

The elements panel, often referred to as the "Inspector," provides a visual representation of the HTML and CSS of a webpage. It allows user to:

- **Inspect and modify HTML elements**: Users can select and inspect individual elements, view their attributes and styles, and make real-time modifications to the page's structure and appearance.
- **Navigate the Document Object Model (DOM)**: The panel displays the hierarchical structure of the webpage's elements, showing how they are nested and organized.
- **Analyze CSS styles**: Users can view and modify the styles applied to elements, including inherited and computed styles, and experiment with different visual presentations.

The elements panel can be used to:

- **Debug layout issues**: Identify and fix visual inconsistencies, layout problems, and overlapping elements by inspecting and modifying the HTML and CSS.
- **Experiment with styles**: Test different visual designs, colors, and layouts by modifying CSS properties and observing the real-time changes on the webpage.
- **Understand webpage structure**: Gain insight into how a webpage is constructed, including the relationships between different elements and their attributes.

### Navigating the DOM

The Code tab displays the DOM as a tree structure, with root elements at the top and nested child elements branching out below. Users can:

- **Expand and collapse branches**: Click on element nodes to expand their children and reveal their sub-structure.
  
- **Filter elements**: Apply filters based on element type, class, ID, or other attributes to focus on specific parts of the DOM.

### Searching for elements

A search bar located at the bottom of the panel allows users to find specific elements based on:

- **Tag name**: Search for all elements of a specific HTML tag (e.g., div, img).

- **Attribute value**: Locate elements with specific values for attributes like `ID` or `class` (e.g., `id="banner"`).

tktk hunter -- maybe ss of search bar? idk what do you think

### Pointer tool

The pointer tool, typically represented by a magnifying glass icon, enables users to:

- **Hover over elements on the webpage**: This highlights the corresponding node in the DOM tree, establishing a visual link between the page and its code.

- **Right-click hovered elements**: Access context menus for inspecting attributes, editing styles, or performing other actions on the selected element.

tktk hunter -- ss of pointer in action

### Benefits of the code tab

- **Debugging layout issues**: Inspecting element properties and relationships within the DOM can help identify the cause of visual inconsistencies or layout problems.

- **Analyzing website structure**: Understanding how elements are nested and connected provides insight into the overall organization and functionality of a webpage.

- **Targeting specific elements**: Precisely selecting elements in the DOM facilitates direct modification of their attributes and styles through the inspector tools.


## Console

The Console panel within Chrome DevTools acts as a powerful interpreter and interactive workspace for JavaScript within the context of a webpage. It allows users to:

- **Execute JavaScript commands**: Send commands directly to the browser to evaluate expressions, run functions, and interact with webpage elements dynamically. 

tktk hunter --  possibly ss of console input field with examples of basic commands

- **Monitor output**: The console displays the results of executed commands, including log messages, errors, and returned values, providing insight into JavaScript execution and webpage behavior. 
  
tktk hunter -- ss of console output with different message types

- **Debug JavaScript**: Set breakpoints in code to pause execution at specific points, examine variable values, and step through code line by line for detailed analysis.

### Using JavaScript in the console
There are a lot of great and helpful ways to use JavaScript in the console. We can:

- **Enter commands directly in the input field**: The console interprets plain JavaScript code, allowing immediate evaluation and interaction with the webpage.

- **Access webpage objects**: Use JavaScript operators and functions to interact with DOM elements, manipulate the page, and explore object properties. 

- **Log messages**: Utilize logging functions like `console.log()` to output information and track the execution flow of your code.

## Network tab

The Network tab within Chrome DevTools serves as a window into the invisible world of communication between your browser and the servers behind webpages. It acts as a digital wiretap, recording and displaying every request and response exchanged during page load and interaction. By analyzing this network traffic, users can gain valuable insights into:

- **Performance analysis**: Identify bottlenecks and slow-loading resources that impact page performance. 
 
tktk hunter -- ss of network waterfall with highlighted slow resources

- **Debugging network issues**: Diagnose connection problems, server errors, and other network-related issues affecting webpage functionality.

- **Understanding resource usage**: Analyze the size and type of resources downloaded, such as images, scripts, and stylesheets, to optimize page load times.

- **Security analysis**: Inspect HTTP headers and security certificates to assess the security posture of network connections.

### Key information in the network tab

- **Request details**: Timestamp, URL, HTTP method (e.g., `GET`, `POST`), status code (e.g., `200 success`, `404 not found`), and requested resource type.

- **Response details**: Response time, size, content type (e.g., image/jpeg, text/html), and headers containing additional information about the response.

- **Timing breakdown**: Visualization of different phases of the request-response cycle, such as DNS lookup, connection establishment, and content download, revealing performance bottlenecks.


### Useful features for network analysis

- **Filtering**: Focus on specific requests based on type, domain, or other criteria for targeted analysis.

- **Sorting**: Organize requests by various parameters like response time, size, or status code for quick identification of potential issues.

- **Exporting data**: Save network log data for further analysis in external tools or sharing with other developers.

### Benefits of the network tab

- **Optimizing website performance**: Identifying and fixing slow-loading resources can significantly improve page load times for users.

- **Troubleshooting website issues**: Network analysis can pinpoint the source of connection problems, server errors, and other issues affecting webpage functionality.

- **Understanding website architecture**: Examining the flow of requests and responses reveals how a website interacts with servers and delivers content.

- **Learning web development**: Analyzing network traffic provides valuable insights into how websites are built and how data is transferred across the web.

## Devices panel

The Devices panel within Chrome DevTools functions as a virtual testing environment for webpages, enabling users to simulate and analyze their layout, functionality, and user experience across diverse device configurations. This facilitates responsive web design practices, ensuring optimal presentation and interaction for users accessing websites on various screen sizes and orientations.

tktk hunter ss of devices panel 

### Key features

- **Device emulation**: A pre-defined library of popular smartphones, tablets, and desktops allows users to select specific device profiles for simulation. Custom dimensions and resolutions can also be configured.

tktk hunter ss of dropdown menu of devices

- **Orientation adjustment**: Portrait, landscape, and other device orientations can be emulated to observe how the webpage layout adapts to different viewing angles.

- **Responsive styling inspection**: Users can analyze how media queries and other responsive design principles are implemented in the webpage's CSS, validating their effectiveness in adapting layouts across devices.

### Testing and analysis

- **Live preview**: The panel displays the webpage adjusted to the chosen device configuration, enabling real-time visualization of layout changes and responsive behavior.

- **Element inspection**: Combined with the Elements panel, users can pinpoint specific elements affected by responsive styling and fine-tune their properties to optimize the layout for different devices.

- **Touch interaction simulation**: Options to emulate tap, swipe, and pinch-to-zoom gestures assist in testing the functionality and user experience of touch-enabled elements on simulated mobile devices.

### Benefits

- **Responsive design validation**: Early identification and rectification of responsiveness issues, such as overlapping elements or truncated content, improve website accessibility and user experience across devices.

- **Layout experimentation**: The ability to preview and adjust layouts in real-time facilitates design iteration and optimization without affecting the live website.

- **Empathy for diverse users**: Understanding how websites appear and function on various devices fosters empathy for users with different screen sizes and interaction preferences, guiding informed design decisions.
