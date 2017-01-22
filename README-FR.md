# minio-gauge
Une jauge d'activité pour Minio avec un Raspberry Pi et un Blinkt! de Pïmoroni, qui montre en temps réel l'activité de votre stockage cloud type S3.

Vous pouvez faire tourner un serveur Minio dans le cloud, sur vos machines, ou même sur un Raspberry Pi. Vous avez juste à configurer les webhooks pour pointer sur votre jauge. De cettez façon on récupère l'activité sur Redis (permet de réduire la latence) et ensuite afficher les couleurs quand les fichiers arrivent.

Ce projet tourne sous Docker et a trois composants :

* Une file Redis
* Un client Webhook (accepte les HTTP POSTs sur le port 3000 et incremente une clé)
* Un pilote d'affichage LED (affecte les couleurs du Blinkt! selon les niveaux)

The pressure display is set to ease off after 2 seconds and goes - green, red, blue.

Checkout the video demo here:

> [Video demo](https://www.youtube.com/watch?v=7lXg3jJs0bU)

### Get ready

Install Docker, pip and Docker-compose

```
# curl -sSL get.docker.com
# apt-get install python-pip
# pip install docker-compose
```

### Get set

```
# docker-compose build
```

This step could take a while, especially on the Pi Zero.

### Go!

```
# docker-compose up -d
```

* Now start the code and find your Raspberry Pi's IP address.
* Edit `~/.minio/config.json` and set your webhook endpoint to the address, i.e. http://raspberrypi.local:3000/

> [Plus de détails en français](http://www.actuino.fr/raspi/jauge-serveur-fichiers.html)
