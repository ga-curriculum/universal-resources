# ![MEN Stack Deployment](./assets/hero.png)

tktk Hunter, this needs a hero!

## Intro

This guide will walk you through deploying a MEN stack application on Heroku.

## What is Heroku? 

In order to make our applications available to the public, we have to store them on an internet server. There are many cloud infrastructure providers that allow developers to use the provider's servers to deploy web apps. 

One of the more popular cloud infrastructure providers is AWS (Amazon Web Services). AWS is the largest cloud infrastructure provider in the world, hosting millions of websites and applications on their servers and giving developers hundreds of services & features to choose from. The learning curve for AWS is intense. 

Heroku is an alternative hosting platform option, although it doesn't own any physical servers like Amazon. Instead, Heroku utilizes Amazon servers but provides developers with a paired down and more intuitive front-end to facilitate the deployment process.

Although the interface is simpler, developers can still host large and powerful web apps using Heroku while having access to many useful features.

## Getting Started with Heroku

GitHub has partnered with Heroku to give GitHub Students free credits to use Heroku's services. To access these credits, you must set up a Heroku Account using GitHub Campus. To set up your Heroku Account using GitHub Campus use the walkthrough below.

### Step 1: Access Your Student Developer Pack

Ensure that you are logged into your personal GitHub account (not GitHub Enterprise) that you provided to General Assembly.

Ensure that you have registered for GitHub Campus with your personal GitHub account. If you have not yet registered for GitHub Campus, follow [tktk this walkthrough].

Navigate to https://education.github.com/pack/offers.

You should now see a page that looks like this:

[]

Scroll down the page until you see the Heroku card, and then click on the card.

[]

You'll be taken to a page like the one shown below. Click on the Get the student offer button.

[]

### Step 2: Sign Up for a Heroku Account

You'll now see one of two pages shown below.

If you see Login Page A, click on the Login with Heroku button to be taken to Login Page B.
If you see Login Page B, click the Sign Up button to register for an account.

[A]|[B]

After clicking Sign Up you'll be taken to a form. Fill it out and then click Create Account.

[]

A new page will appear indicating that an email was sent to the email you provided in the form.

[]

Go to your email and look for the confirmation message sent by `noreply@heroku.com`. Click on the link to activate your account.

The email will open a new Heroku tab in your browser. You can now close out of the previous tab (the page shown in step 2-3). In the new tab, you're prompted to create a password. Once you create your password click the __set password and log in__ button.

[]

On the next page, click the proceed button to continue setting up your account.

[]

### Step 3: Verify Your Student Status

You'll now be taken to the application menu. You'll return here several times. On this page you must first click Verify with GitHub to link your personal GitHub account (now registered with GitHub Campus) with Heroku.

[]

The standard GitHub authorization page will appear. Click Authorize heroku to link your accounts. This will verify you are a student and allow you to deploy projects directly from your GitHub repositories.

[]

### Step 4: Verify Your Billing Information

You'll now be taken back to the application menu to verify your billing information.

❗YOU HAVE FREE CREDITS WORTH $13 USD PER MONTH FOR 12 MONTHS. YOU WON'T BE CHARGED UNLESS YOU EXCEED YOUR CREDITS❗

Verifying your billing information ensures that:

You are a real person
Heroku can charge you if you exceed your credits.
Heroku will also email you reminders as your credits get closer to running out.
Click on Verify my billing information to continue.

[]

A new page detailing the Terms of Service will appear. Read and accept the terms.

[]

You'll get directed to your personal Heroku dashboard. We'll visit this again later. For now, select Add payment method.

[]

You'll find yourself at the Account management page where you can configure your account settings. For now, select Add credit card.

[]

A sidebar will pop out on the left of your screen. Fill out the form and then click Save details.

[]

The sidebar will close and you'll now see your credit card information has been applied to your account.

### Step 5: Finish the Application for Free Heroku Credits

Return to the application menu. Fill out the form and then click send to finish applying for free Heroku credits.

[]

More Terms of Service will appear in a modal. Read and accept the terms.

[]

Your application menu will now have every step completed. It may take 24+ hours to approve the application. You'll receive an email once your application is approved.

[]

You can now return to your Heroku dashboard if you wish. You can use this dashboard to deploy apps once your credits are approved. 

## Deploying a MEN Stack App on Heroku

Today we'll be deploying a MEN stack application to Heroku.

You should already have set up a Heroku account. If not, refer to this [tktk walkthrough] to set one up.
Additionally, you should have set up a MongoDB Atlas account and configured a cluster. If not, refer to this [tktk walkthrough] to set one up.

## Step 1. Configure your MEN Stack Application

### Create a `start` Script

Up until now, we've run our Express apps by executing `npm run dev` which is an NPM script we made that launches our app with nodemon and liveserver to live refresh the app after we make changes to it. While this is ideal for development, when our app is in production (or deployed) we don't need or want it to restart at any point.

Take a look at your `package.json` and ensure there's an NPM script called start.

```json
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node server.js",
    "dev": "nodemon server.js -e css,ejs,js,json"
  },
```

`npm run start` is the default script and entry point to your app. Heroku will execute npm run start when it deploys your application. You can also run this on your machine to test out the production version of your app.

### Create an Environmental Variable

Currently our application has `livereload` packages and middleware that allows us to refresh the page on EJS and CSS file changes. This is very useful for development, but it is unnecessary code to have in a production environment. We're going to create an environment variable that will indicate what environment our application will be running in, so that we can disable the livereload middleware.

In your .env file add this line:

```
ON_HEROKU=false
```

Our Heroku environment will have this same variable, but set to true. By doing this, we can create a conditional that will enable/disable the middleware.

Refactor the middleware section of the `server.js` file so that it looks like this:

```js
// Detect if running in a dev environment
if (process.env.ON_HEROKU === 'false') {
    // Configure the app to refresh the browser when nodemon restarts
    const liveReloadServer = livereload.createServer();
    liveReloadServer.server.once("connection", () => {
        // wait for nodemon to fully restart before refreshing the page
        setTimeout(() => {
        liveReloadServer.refresh("/");
        }, 100);
    });
    app.use(connectLiveReload());
}

// Body parser: used for POST/PUT/PATCH routes: 
// this will take incoming strings from the body that are URL encoded and parse them 
// into an object that can be accessed in the request parameter as a property called body (req.body).
app.use(express.urlencoded({ extended: true }));
app.use(express.static('public'))
// Allows us to interpret POST requests from the browser as another request type: DELETE, PUT, etc.
app.use(methodOverride('_method'));
```

Here, we wrapped our custom middleware in a conditional that will only execute the containing code in a dev environment.

### Step 2: Set up a Heroku MEN Application

Log in to your Heroku account and navigate to the billing section of the site. Make sure you can see the platform credits available to you via GitHub Campus.

Make sure you're subscribed to Eco Dynos to save money. If not yet subscribed, you can just click on the option shown in the image below.

[]

Navigate back to your apps dashboard and select one of the two options shown below to create a new application.

[]

Assign a name to your application. Keep in mind this name will be in the URL Heroku assigns your application.

[]

After creating your application you'll be taken to the application page. From here, navigate to your application settings.

[]

On your application settings page, define your environment variables. You won't need to define a PORT, but you will need to add your MongoDB Atlas connection string. You will also need to add `ON_HEROKU` to `true`.

[][]

You'll also need to tell Heroku what type of application your website will be. We can do that using buildpacks. Underneath your config vars, select the option to add a buildpack.

[]

Select the Node.js buildpack.

### Step 3: Deploy to Heroku from GitHub

Now that your Heroku application is properly configured, it's time to connect your GitHub account and deploy your app from GitHub.

Select the Deploy option in your application page toolbar, select GitHub as your deployment method, and then connect your GitHub account.

[]

Once you've connected your GitHub account, specify which repository you'll use to deploy your application.

[]

Upon selecting your repository, you can select a specific branch to deploy your app from. Enable automatic deploys so that your Heroku app updates every time the branch you selected is pushed to.

[]

Additionally, you can trigger a manual deploy to instantly deploy your application.