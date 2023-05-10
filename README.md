# CORS Proxy Server
This CORS Proxy Server is a simple express app designed to handle api requests 
that need to satisfy a CORS policy when building static HTML/JS applications.

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
To start the server on your local machine run the development script: 
`npm run dev`
- This will start the server by executing the `index.js` file in your local Node 
  environment and ensure dotenv configurations are setup for development mode
- The app is set to listen on PORT: 5001

To use the server make an AJAX request to localhost:5001 and pass a key of `url` 
in the query params set to the url of the api call you would like to make
```js
  fetch("http://localhost:5001/?url=https://catfact.ninja/fact")
    .then(res => res.json())
    .then(res => console.log(res))
```

## Deployment and Use
Once you are done testing locally you may want to have your server hosted to run 
on its own.
- This will prevent the need to run this server locally everytime you want to 
  work on an app that utilizes this server.
- This will also ensure that any apps you have utilizing this server function 
  properly when live hosted.

### Deployment on [Render](render.com)
If you do not already have an account go ahead and sign up

1. From your Render Dashboard let's create a new Web Service
![new-web-service](https://aa-ch-lecture-assets.s3.us-west-1.amazonaws.com/cors-proxy-server/new-web-service.png)

2. If you have not already done so, connect your GitHub account by clicking on 
the `Connect account` link under the GitHub heading and authroizing Render to 
read from your Repositories.
  - Under `Connect a repository` you should now see a list of your GitHub repos

3. Connect to the GitHub repo you set for your CORS Proxy Server
![connect-a-repository](https://aa-ch-lecture-assets.s3.us-west-1.amazonaws.com/cors-proxy-server/connect-a-repopsitory.png)

4. Update the following fields in the resulting form
  - Name: `cors-proxy-server`
  - Region: select the region closest to you
  - Branch: leave as `main`
  - Root Directory: leave as is, even if blank
  - Runtime: Node
  - Build Command: `npm run build`
  - Start Command: `node index.js`
  - Instance Type: Free
  - Click `Create Web Sercice

5. It will take aound 5 minutes for your app to build and deploy. 
  - Once your new web service is Live test it by making a fetch request 
  ```js
    fetch("https://cors-proxy-server.onrender.com/?url=https://catfact.ninja/fact")
      .then(res => res.json())
      .then(res => console.log(res))
  ```

  - you can also test directly on the web service's live page by adding a query
    parameter of `url` and setting it to your desired API request
    - EX: add `?url=https://catfact.ninja/fact` to the url in the browser.

6. Your CORS Proxy Server should now be live and working

NOTES: 
- The dynos for a Render web service go to sleep after 30 minutes
  - If you want to keep them up and running you can setup a cron-job to ping the
    service and keep the app "awake"
  - [Here](https://console.cron-job.org/) is a free and easy to use resource for
    creating cron-jobs. If you don't already have an account signup and follow 
    the setup instrucitons provided.
- Render's free teir offers 750hrs of dyno run time a month. To mitigate running 
  out of dyno hours you can schedule your cron-job to keep the app awake a peak 
  working hours (ex: M-F 9am to 5pm)

## Customization
