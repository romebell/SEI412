# Deploy - Node/MongoDB

## Objectives

* Deploy a Node/Express/MongoDB app to a production server using Heroku
* Use Atlas as the mongo database

## Atlas

First, let's set our app up to use Atlas instead of our local mongo database.

[DOCS](https://docs.atlas.mongodb.com/getting-started/)

1. Create a an account [here](https://account.mongodb.com/account/register)

2. Create a free tier cluster by following [these instructions](https://docs.atlas.mongodb.com/tutorial/deploy-free-tier-cluster/)
 * **NOTE:** Step 3's screenshots haven't been updated so it may look a little different when you do it. Just make sure to choose the *free* tier.
 * **TODO:** Add notes about why you may pick one region over another.
3. Go to Securty > Network Access (from menu on left of page) to [Whitelist your IP address](https://docs.atlas.mongodb.com/tutorial/whitelist-connection-ip-address/)
 * Whitelist your current IP address and also click the *allow access from anywhere* button
4. Go to Security > Database Access to [add a user](https://docs.atlas.mongodb.com/tutorial/create-mongodb-user-for-cluster/)
 * **NOTE:** Make sure you know the password!!!
5. [Connect your cluster](https://docs.atlas.mongodb.com/tutorial/connect-to-your-cluster/):
 * Click "connect", then "connect your application"
 * choose the NodeJS driver for step 1
 * copy the connection string from step 2
 * paste the connection string into your app:
 
```javascript
mongoose.connect(<your connection string> || 'mongodb://localhost/bountyhunters', {
    useNewUrlParser: true, 
    useUnifiedTopology: true,
    useFindAndModify: false
})
```

**Done!** You should see something like the following when you run your Node app locally:

```bash
Connected to MongoDb at bountyhunters-shard-00-02.dwmep.mongodb.net:27017
```

### Protect your connection string

It's a good idea to make your connection string an environment variable, so go ahead and do that too!

```javascript
mongoose.connect(process.env.MONGODB_URI || 'mongodb://localhost/bountyhunters', {
    useNewUrlParser: true, 
    useUnifiedTopology: true,
    useFindAndModify: false
})
```
 
Next, let's deploythe Node app to Heroku.

## Deploying the app

* Create a `Procfile` in the root of your Node application
  * In terminal, run `touch Procfile`. Must be called with a capitol P
  * make sure it is named "Procfile" \(no extention\) 
  * make sure your Procfile is in the same folder as your index.js file
  * in terminal type `echo "web: node index.js" >> Procfile`
* In your `index.js` file, where you get your server started, include the port number in your app.listen function. Example:

```javascript
app.listen(process.env.PORT || 3000)
```

This ensures that when we set the PORT config variable, Heroku will run on it instead of the 3000 port \(Heroku automatically includes a port that's public-facing\).

* Add in your Node version

Note that you may need to specify the node version you're using. To find out what version of node you're using, type the following on your terminal \(from anywhere\):

```text
node -v
```

Then, put the following into your `package.json` file:

```text
"engines": {
    "node": "v11.13.0"
},
```

* Remove the Heroku-Postbuild script if you are launching a decoupled app and it's in your `package.json`.

```text
"scripts": {
    "heroku-postbuild": "There is a bunch of commands here. You can remove this!"
},
```

* Your package.json file is **crucial** - when you deploy your application, Heroku will check the package.json file for all dependencies so be mindful to install any dependencies you may have installed globally. You can always check your package.json to see if you are missing anything.
* Before you create your app in Heroku, be sure your project is being tracked via a git repository.
* Create a Heroku app via the command line

```text
heroku apps:create sitename
```

Where `sitename` is the name of your app. This will create a url like: `http://sitename.herokuapp.com`

* Commit and push all your data at this point \(`git push`\).
* To push to Heroku, enter the following command

```text
git push heroku master
```

* In terminal after you deploy your app, type in `heroku ps:scale web=1`
  * this will scale a dyno up
  
* Go to the heroku website and add the `MONGODB_URI` to your config vars!



