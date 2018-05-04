heroku config:set consumer_key=xxx
heroku config:set consumer_secret=xxx
heroku config:set access_token=xxx
heroku config:set access_token_secret=xxx

Configuring a worker dyno

By default any app deployed to heroku will run in a web dyno, which means, that you can hit it with http requests from the outside. Obviously we do not want that, we just want our bot to run as a background task. Therefore we will shut down the web dyno and spin up a worker dyno for our app instead:

heroku ps:scale web=0 worker=1

In order to spawn a worker dyno, you will need to push a Procfile to your heroku repository as well. Just specify the following startup command in this file and you should be ready to go:

worker: node index.js