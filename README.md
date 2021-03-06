# Tutorial: Deploying a basic Lit app on Jekyo

Demo app [here](https://lit-demo.jekyo.app/)

### Prerequisites

Make sure you have [NodeJS](https://nodejs.org/en/download/), [npm](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) and [git](https://github.com/git-guides/install-git) installed.

If it's your first time using **Jekyo**, you can **install** it by running the following command in your terminal:

`npm install -g jekyo`

### Sign in to Jekyo

You can sign in to Jekyo by running `jekyo user:signin`

```
➜  ~ jekyo user:signin 
Your email?: **************
Your password?: **********
You have successfully signed in!
```
If you don't have a Jekyo account, you can create one in the terminal by running `jekyo user:signup`. 

## 1. Create a basic Lit app

You can start your Lit project by using `jekyo create`

Using the **arrows** on your keyboard, select **lit** and press **enter**.  
```
? Select template
  None Creates only the application
  expressjs A basic app skeleton using [Express](https://expressjs.com/)     
  nuxt-js A boilerplate SSR application using [Nuxt.js](https://nuxtjs.org/) 
❯ lit A basic starter app using [Lit](https://lit.dev/)
```
When prompted, enter the desired name for your Lit app. 

`Application name?: lit-tutorial`

This will create a basic Lit app in the current directory by cloning this [Lit starter app](https://github.com/jekyo/lit-getting-started) repository.

```
Cloning source code... OK
Application created!
```

### Deploy the Lit app on Jekyo

To deploy the app, first navigate to the newly created directory:

`cd lit-tutorial`

Now you can deploy this app to Jekyo by running: 

`jekyo deploy`

After a while, you should see something like this:

```
➜  Fetching source code ... OK
➜  Building application, this might take a while ... OK
➜  Publishing application, this might take a while  ... OK
➜  Deploying application ... OK        
➜  Waiting for application to start ... OK
➜  Visit your app on: https://lit-tutorial.jekyo.app ... OK
```

You can now browse to your Lit app on https://lit-tutorial.jekyo.app (replace 'lit-tutorial' with your app name)

## 2. Deploying an existing Lit app

Navigate to your local Lit app directory

`cd my-lit-app`

Initialize a git repository if you haven't already done so by running `git init`. 

### Edit package.json

Edit the **serve** line under **scripts** to look like this: 

```
"serve": "wds --watch --port $PORT --host $HOST",
```
This specifies the necessary port and host variables for Jekyo.

Add a **start** line: 

```
"start": "MODE=prod npm run serve"
```

### Create an empty Jekyo app:

`jekyo create` 

Select 'none' using the **arrows** on your keyboard and press **enter**. This will create an app using your current directory. 

```
? Select template (Use arrow keys)
❯ None Creates an application from your current directory
```

Name your app: 

`Application name?: my-lit-app`

Run `jekyo link` to link your local app to the remote Jekyo app. Select 'my-lit-app' using the **arrows** on your keyboard and press **enter**.

```
? Select application (Use arrow keys)
❯ my-lit-app
```
### Now you can deploy this app to Jekyo by running: 

`jekyo deploy`

After a while, you should see something like this:

```
➜  Fetching source code ... OK
➜  Building application, this might take a while ... OK
➜  Publishing application, this might take a while  ... OK
➜  Deploying application ... OK        
➜  Waiting for application to start ... OK
➜  Visit your app on: https://my-lit-app.jekyo.app ... OK
```

You can now browse to your Lit app on https://my-lit-app.jekyo.app (replace 'my-lit-app' with your app name)

## Pushing local changes to Jekyo 

Add the newly modified file(s) to the git index by using [git add](https://www.atlassian.com/git/tutorials/saving-changes)

`git add filename`

Create a [git commit](https://github.com/git-guides/git-commit)

`git commit -m "your commit message"`

Now, simply deploy your app again:

`jekyo deploy`

You will see your changes on your live app after a short while. 
