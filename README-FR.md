# minio-gauge
Une jauge d'activité pour Minio avec un Raspberry Pi et un Blinkt! de Pïmoroni, qui montre en temps réel l'activité de votre stockage cloud type S3.

Vous pouvez faire tourner un serveur Minio dans le cloud, sur vos machines, ou même sur un Raspberry Pi. Vous avez juste à configurer les webhooks pour pointer sur votre jauge. De cette façon on récupère l'activité sur Redis (permet de réduire la latence) et ensuite afficher les couleurs quand les fichiers arrivent.

Ce projet tourne sous Docker et a trois composantes :

* Une Queue Redis
* Un client Webhook (accepte les HTTP POSTs sur le port 3000 et incrémente une clé)
* Un pilote d'affichage LED (affecte les couleurs du Blinkt! selon les niveaux)

L'affichage est configuré pour s'atténuer après 2 secondes, et les couleurs sont dans l'ordre : Vert, Rouge, puis Bleu.

Voici la vidéo de démo :

> [Vidéo démo](https://www.youtube.com/watch?v=7lXg3jJs0bU)

### A vos marques

Installez Docker, pip et Docker-compose

```
# curl -sSL get.docker.com
# apt-get install python-pip
# pip install docker-compose
```

### Prêt

```
# docker-compose build
```

Cette étape peut prendre un bout de temps, surtout sur un Pi Zero.

### Partez !

```
# docker-compose up -d
```

* Maintenant lancez le code et trouvez l'adresse IP de votre Raspberry.
* Sur votre serveur Minio, éditez `~/.minio/config.json` et faites pointer votre webhookvers cette adresse, par exemple http://raspberrypi.local:3000/

> [Plus de détails en français](http://www.actuino.fr/raspi/jauge-serveur-fichiers.html)
