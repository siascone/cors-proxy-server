# CORS Proxy Server
This CORS Proxy Server is a simple express app designed to handle api requests that need to satisfy a CORS policy when building static HTML/JS applications.

- [Local Setup](#local-setup)
- [Remote Setup](#remote-setup)
- [Local Use](#local-use)
- [Deployment and Use](#deployment-and-use)
- [Customization](#customization)

## Local Setup
1. Start by either downlading the zip or cloning this repo
2. `cd` into project directory
3. run `npm install`
4. add a `.env` file
  ```.env
    NODE_ENV="development"
  ```
  
## Remote Setup
Following the steps from [Local Setup]() proceed with the following:
1. run `rm -rf .git`
2. run `git init`
3. run `git add .`
4. run `git commit -m 'setup CORS proxy server'
5. create a new GitHub Repository
6. run `git remote add origin <git-url-of-new-GitHub-repo>
7. run `git push -u origin main`

## Local Use
To start the server on your local machine run the development script: `npm run dev`
- This will start the server by executing the `index.js` file in your local Node environment and ensure dotenv configurations are setup for development mode
- The app is set to listen on PORT: 5001

To use the server make an AJAX request to localhost:5001 and pass a key of `url` in the query params set to the url of the api call you would like to make
```js
  fetch("http://localhost:5001/?url=https://catfact.ninja/fact")
    .then(res => res.json())
    .then(res => console.log(res))
```

## Deployment and Use
Once you are done testing locally you may want to have this hosted to run on its own.
- This will prevent the need to run this server locally everytime you want to work on an app that utilizes this server.
- This will also ensure that any apps you have utilizing this server function properly when live hosted.

### Deployment on [Render](render.com)



## Customization
