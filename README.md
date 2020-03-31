# Simple Git Workflow To Deploy Vue app to Firebase
Work for vue app using the firebase sdk app.


## 1. Get Firebase Token
You need to acquire a token from Firebase to allow github to authenticate with the api. 

Simply use the ```firebase login:ci``` command and save the token in your repo Settings/Secrets under the name of ```FIREBASE_TOKEN```.

## 2. Firebase API Token
When you initialize the firebase sdk app you need to provide a api token. You can acquire this token in your firebase console. 
This token must remain secret so you need to store it in your env variables and then import it when you initialize the firebase sdk app like so:
```
firebase.initializeApp({
  apiKey: process.env.VUE_APP_FIREBASE_API_KEY,
  ...
}
```
Save this token in your in your repo Settings/Secrets under the name of ```FIREBASE_API_KEY```.

## 3. Ready to deploy!
Now simply use the provided github action to automatically build and deploy your app whenever you push content in your master branche. 

In you want to use another branche to trigger the deploy, change the ```master``` in the following code for the name of your branche.
```
on:
  push:
    branches: [ master ]
  pull_request:
    branches: [ master ]
```