Drupal Demo Site Running on Lagoon
===========================================

Requirements
------------

  * [Using Lagoon - The Basics][1]
  * [The Lagoon CLI][3] (If you intend to access the project remotely)

Installation
------------

You'll need pygmy to run the demo locally. See [Local Development Environments][4]

Usage - Local
-------------

There's no need to configure anything to run the application. If you have
[Local Development Running][2] binary, run this command:

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
- Branch `dev` are also configured to deploy
- To ssh to the `cli` container: `lagoon ssh -p demo-tag1-drupal -e main` 
  -  `main` can be replaced with `dev` 

Support
-------
Feel free to jump into the tag1 agency channel on amazeeio.rocket.chat or Slack! 


[1]: https://docs.lagoon.sh/using-lagoon-the-basics
[2]: https://docs.lagoon.sh/using-lagoon-the-basics/local-development-environments/
[3]: https://docs.lagoon.sh/installing-lagoon/lagoon-cli/
