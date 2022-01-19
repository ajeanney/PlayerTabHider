# PlayerTabHider

Cachez les joueurs que vous listez de la tab list et du nombre de joueurs du serveur, directement depuis un fichier de configuration, sans rien à installer côté client.

## Fonctionnalités

- Les joueurs nommés dans la configuration disparaissent de la tab list dès que quelqu'un se connecte.
- Ils sont aussi cachés du ping de la liste des serveurs : ils sont retirés de l'échantillon de joueurs et le nombre de joueurs en ligne est diminué, l'écran multijoueur affiche donc les mêmes chiffres que le jeu lui-même.
- Uniquement côté serveur : c'est un mod Fabric basé sur des mixins, un client vanilla voit donc le résultat sans rien installer.
- Rien n'est codé en dur : la liste des noms cachés et l'activation se trouvent dans `config/playertabhider.json`.

## Prérequis

- Un **serveur** Minecraft 1.18.x avec Fabric Loader 0.11.3 ou supérieur, sous Java 17.
- [Fiber](https://github.com/FabLabsMC/fiber), la bibliothèque de configuration : elle est incluse dans le jar compilé, il n'y a donc rien à installer à côté du mod.

## Installation

1. Compilez le mod (voir plus bas) et déposez le jar dans le dossier `mods/` de votre serveur Fabric.
2. Démarrez le serveur une fois : `config/playertabhider.json` est créé.
3. Ajoutez les noms à cacher dans ce fichier et redémarrez le serveur.

## Configuration

```json
{
  "hide_players": {
    "enabled": true,
    "value": ["Bot"]
  }
}
```

- `enabled` : si les joueurs sont cachés ou non.
- `value` : les noms des joueurs à cacher.

Le fichier est lu au démarrage du serveur, et réécrit avec les valeurs par défaut s'il est absent ou illisible.

## Compilation

```sh
./gradlew build
```

Le mod est écrit dans `build/libs/`. Il est compilé contre Minecraft 1.18.1, et les versions utilisées sont celles de `gradle.properties`.
