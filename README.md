# NGiNX és PHP 8.1 webszerver docker alapokon

## Telepítés

Hozzon létre egy `www` mappát. Az oldal tartalma ide kerüljön, ez lesz a gyökérkönyvtár.
A weboldal tartalmát a későbbiekben majd ide kell belemásolni.

Másolja le a `.env-example` fájlt `.env` néven. Amennyiben szükséges állítsa be portot (`PORT_WEB`).

## Indítás

Telepítéstől függően `docker-compose` vagy `docker compose` használata szükséges.

```bash
docker-compose -f docker-compose.yml -f docker-compose.dev.yml up -d
```

A `-f` kapcsoló szabja meg, hogy melyik fájl alapján induljon el minden. Többször is kiadható, ilyenkor az azonos értékek felülíródnak a megadási sorrend szerint!

Az `up` indítja el a konténereket, ha még nem volt build, akkor a build is lefut.

A `-d` hatására a háttérben indul, visszakapjuk a konzolt.

## Hibakeresés

Hiba esetén a `docker-compose logs` által lehet megtekinteni a konténerek által logolt adatokat.

## Etc

`docker compose exec php fish` open shell

if json exists do `composer install`

else `composer require filp/whoops`

and `composer dump-autoload -o` (to autoload classes)

import whoops in php:
```
require_once('./vendor/autoload.php'); 
$whoops = new \Whoops\Run;
$whoops->pushHandler(new \Whoops\Handler\PrettyPageHandler);
$whoops->register();
```

composer.json : Uses psr-4
```
"autoload": {
        "psr-4": {
            "NameSpace\\" : "src/NameSpace"
        }
    }
```
