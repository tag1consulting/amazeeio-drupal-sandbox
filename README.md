Symfony Demo Application Running on Lagoon
===========================================

Requirements
------------

  * [Using Lagoon - The Basics][3]
  * [The Lagoon CLI][5] (If you intend to access the project remotely)

Installation
------------

You'll need pygmy to run the demo locally. See [Local Development Environments][4]

Usage - Local
-------------

There's no need to configure anything to run the application. If you have
[Local Development Running][4] binary, run this command:

```bash
$ cd amazeeio-drupal-sandbox/
$ docker-compose build
$ docker-compose run cli bash 
## Now in Docker
$ COMPOSER_MEMORY_LIMIT=-1 composer --no-ansi --no-interaction install --no-progress
$ exit
## Now back on your local
$ docker-compose up
```

Then access the application in your browser at http://demo-tag1-drupal.docker.amazee.io

Usage - on amazee.io
---------------------

- The project is deployed to amazee.io and can be seen at https://nginx.main.demo-tag1-drupal.us2.amazee.io
- Push changes to the main branch to get a new deployment going
- Branches `dev` and `staging` are also configured to deploy
- To ssh to the `cli` container: `lagoon ssh -p demo-tag1-drupal -e main` 
  -  `main` can be replaced with `dev` or `staging`

Support
-------
Feel free to jump into the tag1 agency channel on amazeeio.rocket.chat! 

TODO
----
In order to make this demo production ready, there are a few outstanding issues to resolve

!!! NB: DO NOT USE THIS CONFIGURATION IN PRODUCTION!! 

1. Symfony is unhappy about either the way Nginx proxies to PHP-FPM, or the way there is no https locally, and so the session cookie is not being sent. To work around this for the demo, cookie values are set to insecure in framework.yml. 

2. There are no cron-jobs or deployment tasks configured

3. Session storage is using local storage, and could be connected to REDIS or the DB for more advanced session management

4. Persistent file storage is not configured at this stage (would be application specific)


[1]: https://symfony.com/doc/current/best_practices.html
[2]: https://symfony.com/book
[3]: https://docs.lagoon.sh/using-lagoon-the-basics
[4]: https://docs.lagoon.sh/using-lagoon-the-basics/local-development-environments/
[5]: https://docs.lagoon.sh/installing-lagoon/lagoon-cli/
