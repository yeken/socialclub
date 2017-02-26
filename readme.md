#DEVELOPMENT ENVIRONMENT
Base code is written in [Laravel 5.4](https://laravel.com/docs/5.4/), so whatever your server choice is it must [meet the server requirements](https://laravel.com/docs/5.4#server-requirements) for development.
We recommend the use of [Homestead vagrant box](https://laravel.com/docs/5.4/homestead), there is good article on how to install it [here](https://scotch.io/tutorials/getting-started-with-laravel-homestead).

Once server is set, you should have a `local.PROJECTNAME.com` url pointing to your Laravel instance. 


#INSTALL REPO

##1) configure your [GitHub account](https://help.github.com/articles/set-up-git/) and [Fork the repo to your own account](https://help.github.com/articles/fork-a-repo/)

##2) create an `.env` file from `env.example`, update composer by running `composer update` on your root folder and then `php artisan migrate` to migrate the whole DB.

##3) You’ll probably need the `public/storage` folder or one of the kind, should download via FTP from staging server or production server.

#ISSUES FLOW

The flow idea is that you work a _branch_ on your *fork* and then make PRs to *original repository* (called _upstream_)

So when you start working on an issue (or _branch_):
```
cd [local project root folder]
git checkout -b NEW_BRANCH_NAME
```
Will create the new branch. Next step make sure your fork is up to date:
```
git pull —rebase upstream staging
```
Do your thing. Make all the changes you want and then
```
git add -A .
```
Will add all the files you’ve worked on
```
git commit -m “MESSAGE_HERE”
```
Will commit the changes.
```
git pull —rebase upstream staging
```
`pull` code from *original repository* (`upstream`, `staging` branch) and `—rebase` so that your code is on top.
IMPORTANT: Fix all conflicts, if any.
```
git push origin NEW_BRANCH_NAME
```
Will push your code to your *fork*.

You then need to [create a pull request](https://help.github.com/articles/about-pull-requests/)
