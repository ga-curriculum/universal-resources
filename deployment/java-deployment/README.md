# ![Java Deployment](./assets/tktk-hero.png)

## Intro

This guide will walk you through deploying a Java application to Heroku.

## Getting started (don't skip this, this is important!)

To begin, you'll need:

- A Heroku account. Follow the [Getting Started with Heroku](../getting-started-with-heroku/README.md) guide to walk you through this if you haven't already. You should be signed in to this account.
- A Java app that starts and runs ***without warnings or errors***.

## Prepare your Java app for deployment

We will need to to a couple of things to your application before we can deploy it to Heroku.

### Create your JAR file

Before you can deploy your Java application to Heroku, you'll need to create a JAR file. This file will contain all of the necessary code and resources for your application to run.

1. Click File -> Project Structure
2. Navigate to Artifacts under Project Settings
3. Click "+"
4. Select JAR -> Choose "From modules with Dependencies"
5. Select your Main class
6. Click OK
7. Click Build -> Build Artifacts
8. Click Build

Keep in mind the name of the JAR file you created. You'll need this later.

### Add a Procfile

A `Procfile` is a file that tells Heroku how to run your application. Create a file named `Procfile` in the root of your project and add the following line:

```plaintext
web: java -jar <your-jar-file-name>.jar
```

Once you have created your `Procfile`, add, commit, and push your changes to GitHub.

## Deploying a Java application with Heroku

Log in to your Heroku account and navigate to the billing section of the site. Make sure you can see the platform credits available to you via GitHub Campus.

> Make sure you're subscribed to Eco Dynos to save money. If not yet subscribed, you can go to the billing section and click to subscribe.

From your Heroku dashboard, select the option to create a new app.

1. Click the "New" button in the top right corner of the dashboard.
2. Select "Create new app" from the dropdown menu.
3. Assign a name to your application. Keep in mind this name will be in the URL Heroku assigns your application.
4. Click the "Create app" button.

After creating your application you'll be taken to the application page. From here, navigate to your application settings.

Under the Config Vars section, select the "Reveal Config Vars" button. Once you've done this, you will see a place to add your environment variables. Add all of the environment variables your application needs to run.

> This will be all of the environment variables you have in your `.env` file.

After you have added your environment variables, go the the Buildpacks section of your application settings. Add the Java buildpack to your application.

Once you have added the Java buildpack, you can connect your GitHub account to your Heroku application. Select the Deploy option in your application page toolbar, select GitHub as your deployment method, and then connect your GitHub account.

Once you've connected your GitHub account, specify which repository you'll use to deploy your application.

You can select a specific branch to deploy your app from. Enable automatic deploys so that your Heroku app updates every time the branch you selected is pushed to.

That's it! Your application is now deployed to Heroku.
