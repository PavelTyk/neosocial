NeoSocial
=========

Example application to connect Neo4j to Facebook using the Neography Gem.


Pre-Requisites
--------------

* You will need to get a Facebook Consumer Key and Secret on https://developers.facebook.com/apps
* Select the "user_likes", "user_location", "friend_likes", "friend_location" permissions.
* You will need Neo4j in order for your database.
* You will need Redis in order to use Sidekiq for background jobs.

Installation
----------------

    git clone git@github.com:maxdemarzi/neosocial.git
    bundle install
    sudo apt-get install redis-server or brew install redis
    rake neo4j:install['enterprise','1.8.M07']
    rake neo4j:start
    export SESSION_SECRET=<your session secret>
    export FACEBOOK_APP_ID=<your facebook app id>
    export FACEBOOK_SECRET=<your facebook secret>
    export REDISTOGO_URL="redis://127.0.0.1:6379/"
    foreman start

On Heroku
---------

    git clone git@github.com:maxdemarzi/neosocial.git
    heroku apps:create neosocial
    heroku config:add SESSION_SECRET=<your session secret>
    heroku config:add FACEBOOK_APP_ID=<your facebook app id>
    heroku config:add FACEBOOK_SECRET=<your facebook secret>
    heroku addons:add neo4j
    heroku addons:add redistogo
    git push heroku master
    heroku ps:scale worker=1

See it running live at http://neosocial.heroku.com
