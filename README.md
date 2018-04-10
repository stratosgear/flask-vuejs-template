# Flask-vuejs-template

This project is supposed to serve a nuxt SPA app from a Flask server.

It is based on a sample project template [flask-vuejs-template](https://github.com/gtalarico/flask-vuejs-template) that was using a simple non-nuxt vuejs app

## Application Structure

The project is a Flask application with with two blueprints:

1. Api App: Blueprint uses FlaskRestful to serve resources at the `/api` url endpoint (Not used in this example)
2. Client App: Minimal Blueprint used only to serve a single-page Vue.js App at the root endpoint `/`


#### Vue.js Structure (Client App)

The nuxt.js application is served by the Client App Blueprint.

This template assumes you want to use VueJs to manage all of your front-end resources and assets,
so it does not attempt to overwrite Jinja's or Vue's template delimiter.  It is just serving the SPA app as it generated by the `npm run build` command.

The nuxt.js app is based in the minimal SPA example app taken straight out of the [nuxt.js examples](https://github.com/nuxt/nuxt.js/tree/dev/examples/spa)


## Installation

1. Clone Repository
1. cd to your repo 
1. I'm assuming you have [pipenv](https://docs.pipenv.org/) installed (better/easier virtualenvs)
1. `pipenv install` to install all python dependencies
1. `cd nuxt` to get to your nuxt app
1. `npm install` to install all node js packages
1. `npm run build` to build the SPA app.
1. `cd ..` to get to the root of the Flask app
1. `pipenv run python run.py` to start the Flask server


## Files produced

Normally these files would not be included in the git repo (since they can be automatically produced by the development tools) but I left them in so you can take a look without having to checkout and run everything.

The `nuxt.config.js` has been configured to output all generated frontend files in the `/app/static/spa` folder. Nuxt **still** outputs a duplicate set of files in `/nuxt/dist`, although at this point it's not as important of an issue.

# Problem

After visiting `http://localhost:5000` you will be greeted with a **blank page**.  Viewing the page source displays:

```
<!DOCTYPE html>
<html >
  <head>
    
  </head>
  <body >
    
  <script type="text/javascript" src="/static/spa/dist/manifest.04f57aedf746913dca1f.js"></script><script type="text/javascript" src="/static/spa/dist/vendor.e5846097588ab215ec84.js"></script><script type="text/javascript" src="/static/spa/dist/app.4305fc29686149ef8b58.js"></script></body>
</html>
```

All the `/static/spa/dist/*.js` files are served properly as `webpackJsonp` compressed files.

Chrome's developer tools console does **not** display any errors.

What I'm I doing wrong?
