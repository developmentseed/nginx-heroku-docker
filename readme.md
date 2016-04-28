# NGINX Binary for Docker in Heroku

This docker app compiles a NGINX binary ready for use and deployment as a Docker app on Heroku. The binary is compiled against Heroku's Cedar-14 stack.

If you want to run NGINX proxy on Heroku's managed environment, this is app is what you need.

In order to use this app, you must have Heroku plugin for docker and docker installed on your computer. You can follow [this guide](https://devcenter.heroku.com/articles/introduction-local-development-with-docker?preview=1) to have the requirements installed.

## Recompile nginx binary for Cedar-14

Make sure you have docker and docker-composed installed. Run this command:

    $ docker-compose build web
    $ docker-compose up web

After the command is executed, nginx's binary is copied to `heroku/bin` folder.

## Use and Deployment of NGINX

After executing the previous step, simply copy the heroku folder to a new location and use it for launching and deploying a heroku app.

To deploy a new heroku app using the content of `heroku` folder:

```bash
$ heroku create
$ heroku docker:release
$ heroku logs -t
```

## NGINX Config

Edit content of `heroku/config/nginx.conf.erb`.

## Credit

- [nginx-buildpack](https://github.com/ryandotsmith/nginx-buildpack)
